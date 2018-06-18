## Collectd/Restart-collectd-if-needed

This role makes sure collectd is restarted in case fluentd service is up,
even if there was no configuration change to collectd itself.

In addition, the role checks if collectd is active at the end and print the result.
