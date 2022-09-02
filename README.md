# metrics
![CI Testing](https://github.com/linux-system-roles/metrics/workflows/tox/badge.svg)

An ansible role which configures performance analysis services for the managed
host.  This (optionally) includes a list of remote systems to be monitored
by the managed host.

## Requirements

Performance Co-Pilot (PCP) v5+. All of the packages are available
from the standard repositories on Fedora, CentOS 8, and RHEL 8.  On RHEL
7 and RHEL 6, you will need to enable the Optional repository/channel
on the managed host.

The role can optionally use Grafana v6+ (`metrics_graph_service`) and
Redis v5+ (`metrics_query_service`) on Fedora, CentOS 8, RHEL 8 and later.

The role requires the `firewall` role and the `selinux` role from the
`fedora.linux_system_roles` collection, if `metrics_manage_firewall`
and `metrics_manage_selinux` is set to true, respectively.
(Please see also the variables in the [`Role Variables`](#role-variables) section.)

If the `metrics` is a role from the `fedora.linux_system_roles`
collection or from the Fedora RPM package, the requirement is already
satisfied.

Otherwise, please run the following command line to install the collection.
```
ansible-galaxy collection install -r meta/collection-requirements.yml
```

## Role Variables

    metrics_monitored_hosts: []

List of remote hosts to be analysed by the managed host.
These hosts will have metrics recorded on the managed host, so care should be
taken to ensure sufficient disk space exists below /var/log for each host.

Example:

```yaml
metrics_monitored_hosts: ["webserver.example.com", "database.example.com"]
```

    metrics_retention_days: 14

Retain historical performance data for the specified number of days; after
this time it will be removed (day by day).

    metrics_graph_service: no

Boolean flag allowing host to be setup with graphing services.
Enabling this starts PCP and Grafana servers for visualizing PCP metrics.
This option requires Grafana v6+ which is available on Fedora, CentOS 8,
RHEL 8, or later versions of these platforms.

    metrics_query_service: no

Boolean flag allowing host to be setup with time series query services.
Enabling this starts PCP and Redis servers for querying recorded PCP metrics.
This option requires Redis v5+ which is available on Fedora, CentOS 8,
RHEL 8, or later versions of these platforms.

    metrics_into_elasticsearch: no

Boolean flag allowing metric values to be exported into Elasticsearch.

    metrics_from_elasticsearch: no

Boolean flag allowing metrics from Elasticsearch to be made available.

    metrics_from_postfix: no

Boolean flag allowing metrics from Postfix to be made available.

    metrics_from_mssql: no

Boolean flag allowing metrics from SQL Server to be made available.
Enabling this flag requires a 'trusted' connection to SQL Server.

    metrics_from_bpftrace: no

Boolean flag allowing metrics from bpftrace to be made available.

    metrics_username: metrics
    metrics_password: metrics

Mandatory authentication for executing dynamic bpftrace scripts.

    metrics_provider: pcp

The metrics collector to use to provide metrics.

Currently Performance Co-Pilot is the only supported metrics provider.
When using the PCP provider these TCP ports will be used - 44321 (pmcd,
live metric value sampling), 44322 (pmproxy, with metrics_query_service
or metrics_graph_service), 6379 (redis-server for metrics_query_service)
and 3000 (grafana-server for metrics_graph_service).

    metrics_manage_firewall: false

Boolean flag allowing to configure firewall using the firewall role.
Manage the pmcd port, the pmproxy port, the Grafana port and the Redis
port depending upon the configuration parameters.
If the variable is set to false, the `metrics role` does not manage the
firewall.

NOTE: `metrics_manage_firewall` is limited to *adding* ports.
It cannot be used for *removing* ports.
If you want to remove ports, you will need to use the firewall system
role directly.

NOTE: the firewall management is not supported on RHEL 6.

    metrics_manage_selinux: false

Boolean flag allowing to configure selinux using the selinux role.
Assign the pmcd port, the pmproxy port, the Grafana port and the Redis
port depending upon the configuration parameters.
If the variable is set to false, the `metrics role` does not manage the
selinux.

Please note that the pmcd and pmproxy services are in the "ephemeral"
range requiring no special setup and the Grafana port is "unregistered".
The Redis port is gated by the redis_port_t SELinux type and may need to
be further configured, if you require direct access (not required if you
are accessing it from metrics role tools like Grafana and PCP).
Use https://github.com/linux-system-roles/selinux to manage port access,
for SELinux contexts.

NOTE: `metrics_manage_selinux` is limited to *adding* policy.
It cannot be used for *removing* policy.
If you want to remove policy, you will need to use the selinux system
role directly.

## Dependencies

None.

## Example Playbook

Basic metric recording setup for each managed host only, with one
weeks worth of data retained before culling.

```yaml
- hosts: all
  vars:
    metrics_retention_days: 7
  roles:
    - linux-system-roles.metrics
```

Scalable metric recording, analysis and visualization setup for
the managed hosts, providing a REST API server with an OpenMetrics
endpoint, graphs and scalable querying.

```yaml
- hosts: all
  vars:
    metrics_graph_service: yes
    metrics_query_service: yes
  roles:
    - linux-system-roles.metrics
```

Centralized metric recording setup for several remote hosts and
scalable metric recording, analysis and visualization setup for
the local host, providing a REST API server with an OpenMetrics
endpoint, graphs and scalable querying.

```yaml
- hosts: monitors
  vars:
    metrics_monitored_hosts: [app.example.com, db.example.com, nas.example.com]
    metrics_graph_service: yes
    metrics_query_service: yes
  roles:
    - linux-system-roles.metrics
```

## License

MIT
