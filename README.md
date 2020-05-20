# Role Name

An ansible role which configures performance analysis services for the local
system.  This (optionally) includes a list of remote systems to be monitored
by the local system.

## Requirements

Uses features of Performance Co-Pilot (PCP) v5+, Grafana v6+, and Redis v5+.

## Role Variables

    monitored_hosts: []

List of remote hosts to be analysed by the target host.
These hosts will have metrics recorded on the target host, so care should be
taken to ensure sufficient disk space exists below /var/log for each host.

Example of setting the variables:

```yaml
monitored_hosts: ["webserver.acme.com", "database.acme.com"]
```

    with_graph_service: false

Boolean flag allowing host to be setup with graphing services.
Enabling this starts PCP and grafana servers for visualizing PCP metrics.

    with_query_service: false

Boolean flag allowing host to be setup with time series query services.
Enabling this starts PCP and redis servers for querying recorded PCP metrics.

## Dependencies

None.

## Example Playbook

Basic metric recording setup for the local host only, with one
weeks worth of data retained before culling.

```yaml
- hosts: all
  vars:
    retention_days: 7
  roles:
    - linux-system-roles.metrics
```

Scalable metric recording, analysis and visualization setup for
the local host, providing a REST API server with an OpenMetrics
endpoint, graphs and scalable querying.

```yaml
- hosts: all
  vars:
    with_graph_service: true
    with_query_service: true
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
    monitored_hosts: [app.acme.com, db.acme.com, nas.acme.com]
    with_graph_service: true
    with_query_service: true
  roles:
    - linux-system-roles.metrics
```


## License

MIT

## Author Information

Maintained by Shirly Radco <sradco@redhat.com>, Nathan Scott <nathans@redhat.com>,
Peter Portante <portante@redhat.com> and Andreas Gerstmayr <agerstmayr@redhat.com>
