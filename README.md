Metrics
====================

The `metrics` role enables you to deploy and configure metrics collectors, trasformators and shippers.

Role Variables
--------------

### Configure metrics
In order to run this role you will need set the following variables:

- `env_name:` (required - default: `"engine"`)

  Environment name. Is used to identify the source of the collected data.

- `fluentd_elasticsearch_host:` (required - no default value)

  Address or hostname (FQDN) of the Elasticsearch server host.

- `env_uuid_metrics:` (required - no default value)

  UUID of the project/namespace used to store metrics records.
  This is used to construct the index name in Elasticsearch.
  For example, if you have env_name: myenvname,
  then in logging OpenShift you will have a project named metrics-myenvname.
  You need to get the UUID of this project like this:
  oc get project metrics-myenvname -o jsonpath='{.metadata.uid}'


In order to set these variable add the required variables to the config.yml
or in the command line.

You don't need to update the configuration file if you wish to use default options.

License
-------

Apache License 2.0

