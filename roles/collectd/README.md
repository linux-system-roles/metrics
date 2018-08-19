## oVirt.ovirt-initial-validations/ovirt-include-vars-files

This role includes the config.yml file, if it exists and
also includes the `config.yml.d` directory,
where additional var files can be added.

The available variables for this role are:

- `collectd_service_name:`  (default: `"collectd"`)

- `ovirt_metrics_pkg_sysconf_dir:`(default: `/etc/ovirt-engine-metrics`)

  The ovirt-engine-metrics configuration information directory path

- `ovirt_metrics_config_yml_dir:`(default: `"{{ ovirt_metrics_pkg_sysconf_dir }}/config.yml.d"`)

  The path to the `config.yml.d` directory, where additional var files can be added.

- `ovirt_metrics_config_yml_file:`(default: `"{{ ovirt_metrics_pkg_sysconf_dir }}/config.yml"`)

  The ovirt-engine-metrics config.yml file path.

- `collectd_interval:`  (default: `"10"`)

   It controls the collection interval of the statistics.

- `collectd_write_http_host:`  (default: `"localhost"`)

  The host that collectd will write to using http

- `collectd_write_http_port:` (default: `"9880"`)

  The port that collectd will write to using http. This is the default
  port on which fluentd listens for http data.

- `collectd_write_http_url:`
  (default: `"http://{{ collectd_write_http_host }}:
  {{ collectd_write_http_port }}/{{ collectd_write_http_path }}"`)

  The full URL that collectd will write to. Usually should not be changed.

