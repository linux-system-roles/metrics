## oVirt.ovirt-collectd/Write-http

This role configures collectd to send the metrics by http.

The available variables for this role are:

- `collectd_write_http_host:`  (default: `"localhost"`)

  The host that collectd will write to using http

- `collectd_write_http_port:` (default: `"9880"`)

  The port that collectd will write to using http. This is the default
  port on which fluentd listens for http data.

- `collectd_write_http_url:`
  (default: `"http://{{ collectd_write_http_host }}:
  {{ collectd_write_http_port }}/{{ collectd_write_http_path }}"`)

  The full URL that collectd will write to. Usually should not be changed.
