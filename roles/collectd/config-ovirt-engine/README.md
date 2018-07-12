## oVirt.ovirt-collectd/Config-ovirt-engine

This role loads and configures oVirt engine collectd plugins.
collectd gathers oVirt statistics from the oVirt engine and hypervisors, and transfers the data to fluentd.

The data is then transformed, enriched, and sent to the remote metrics store.

oVirt Metrics - collectd loaded plugins list and configurations:

- `disk`

  Disk utilization: Sectors read/written, number of read/write actions, average time an IO-operation took to complete.

- `cpu`

  CPU time spent in the system, user, nice, idle, wait, interrupt, softirq and steal.

- `memory`

  Collects information about the used, buffered, cached and free RAM memory.

- `load`

  The average number of runnable tasks in the run-queue, for one, five, and fifteen minute average.

- `nfs`

  NFS usage: A count of the number of procedure calls for each procedure,
  grouped by version and whether the system runs as a server or client.
  NFS version 4 is not supported for now.

- `entropy`

  Amount of entropy available to the system.

- `swap`

  Records the free, cached, and used memory utilized by swap and swap in/out.

- `df`

  Collects file system (incl. the hard drive) usage information such as free, reserved, and used space.

- `interface`

  Collects network traffic download and upload data, including the number of octets, packets, and errors
  transmitted and received for each network interface.

- `aggregation`

  Aggregates multiple values into a single value, using one or several consolidation functions,
  e.g. summation and average.

  Aggregations:

  - CPU percent per host and TypeInstance (system, user, nice, idle, wait, interrupt, softirq and steal)

- `processes`

  Collects the number of processes, grouped by their state
  (incl. running, blocked, sleeping, paging, stopped and zombies).

  Process "fluentd"
  Process "collectd"
  ProcessMatch "ovirt-engine" "ovirt-engine\.xml"

- `uptime`

  Keeps track of the system uptime, providing informations such as the average running time or
  the maximum reached uptime over a certain period of time.

- `postgres`

  PostgreSQL database statistics: custom_deadlocks, table_states, disk_io, disk_usage.

The available variables for this role are:

- `configure_collectd_postgresql:`  (default: `"true"`)

  Whether to configure collectd_postgresql


In order to set these variable add the required variables to the config.yml
or in the command line.


For a full documentation of each plugin, please refer to collectd man pages:
<https://collectd.org/documentation/manpages/collectd.conf.5>
