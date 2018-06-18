## Collectd/Collectd-setup

This role enables the service, sets collectd_tcp_network_connect
and stops the service if fluentd is not running.

It also configures collectd top-level configuration flie.

The available variables for this role are:

- `collectd_interval:`  (default: `"10"`)

   It controls the collection interval of the statistics.


In order to set these variables, add the required variables to the config.yml
or in the command line.

You don't need to update the configuration file if you wish to use default options.
