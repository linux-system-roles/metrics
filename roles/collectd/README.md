## collectd

This role runs dependent collectd roles, Roles list is located in the meta directory.

It is run as part of the `Configure Metrics` play and the default `configure` tag.
It also includes the `restart collectd` handler.


The available variables for this role are:

- `collectd_service_name:`  (default: `"collectd"`)

  Collectd service name.


In order to set these variable add the required variables to the config.yml
or in the command line.

You don't need to update the configuration file if you wish to use default options.
