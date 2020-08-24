# metrics

An ansible role which configures performance analysis services for the managed
host.  This (optionally) includes a list of remote systems to be monitored
by the managed host.

## Requirements

Performance Co-Pilot (PCP) v5+. All of the packages are available
from the standard repositories on Fedora, CentOS 8, and RHEL 8.  On RHEL
7 and RHEL 6, you will need to enable the Optional repository/channel
on the managed host.

The role can optionally use Grafana v6+ (`metrics_graph_service`) and
Redis v5+ (`metrics_query_service`) on Fedora, CentOS 8, and RHEL 8.

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
Enabling this starts PCP and grafana servers for visualizing PCP metrics.

    metrics_query_service: no

Boolean flag allowing host to be setup with time series query services.
Enabling this starts PCP and redis servers for querying recorded PCP metrics.

    metrics_provider: pcp

The metrics collector to use to provide metrics.
Currently Performance Co-Pilot is the only supported metrics provider.


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

## Author Information

Maintained by Shirly Radco <sradco@redhat.com>, Nathan Scott <nathans@redhat.com>,
Peter Portante <portante@redhat.com> and Andreas Gerstmayr <agerstmayr@redhat.com>
