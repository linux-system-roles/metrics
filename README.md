linux-system-roles Metrics
==========================

Guidelines for Using Metrics Ansible Role
-----------------------------------------

The `metrics` role enables a RHEL admin/developer to deploy metrics collectors on the local host, remote host or set of remote hosts,
process these metrics if needed to add additional metadata and ship it to a remote location to be saved and analyzed.

The default setup is PCP metrics collector saved to local machine.

Definitions
-----------

  - [`PCP`](https://pcp.io/) - The metrics role default log collector used for metrics collection.
  - [`Collectd`](https://collectd.org/) - Collectd collects system and application performance metrics, and can be used in a or instead of the default collector.
  - [`Viaq`](https://docs.okd.io/latest/install_config/aggregate_logging.html)- Common Logging based on OpenShift Aggregated Logging (OCP/Origin).
  - [`Elasticsearch`](https://www.elastic.co/) - Non-OpenShift standalone Elasticsearch.
  - `Local` - Output the collected metrics to a local File/Journal.
  - `Message Queue` (kafka, amqp) - Not yet supported.

Deploy Default Metrics Configuration Files
==========================================


``` ansible-playbook [-vvv]  --become --become-user root --connection local -i inventory_file playbook.yaml ```

Deploy Configuration Files
===========================

Typical ansible-playbook command line.

``` ansible-playbook [-vvv] -e@vars.yaml --become --become-user root --connection local -i inventory_file playbook.yaml ```

Two files - inventory_file and vars.yaml - in the command line is to be updated by the user.

Inventory File
--------------
inventory_file is used to specify the hosts to deploy the configuration files.

   Sample inventory file for the es-ops enabled case
```
[masters]
localhost ansible_user=YOUR_ANSIBLE_USER

[nodes]
localhost ansible_user=YOUR_ANSIBLE_USER
```

Deploy Default Metrics Configuration Files
------------------------------------------

For default metrics configuration files, add the inventory_file and run the ansible playbook without the vars.yaml file.

``` ansible-playbook [-vvv]  --become --become-user root --connection local -i inventory_file playbook.yaml ```

No additional steps required.

vars.yaml
---------

vars.yaml stores variables which are passed to ansible to control the tasks.

Initial conf will be supplied by default.
User can supply another conf to be used.

Configure the list of outputs you want to send your metrics to.


vars.yaml example:

```
metrics_output_list:
  - name: ovirt-elasticsearch
    type: elasticsearch
    metrics_collections: [ 'ovirt' ]
    server_host: logging-es-ovirt
    server_port: 9200
    index_prefix: project.ovirt-logs
    ca_cert:
    cert:
    key:
  - name: local-example
    type: local
    metrics_collections: [ 'example' ]
  - name: custom_files-test
    type: custom_files
    custom_config_files: [ '/path/to/custom_A.conf', '/path/to/custom_B.conf' ]
```

   See the variables section for each variable.

**Note:** The order of the record with type  `elasticsearch` is important. The last Elasticsearch output will get all the metrics that were not cached by previous Elasticsearches instances.

playbook.yaml
-------------

- name: install and configure metrics on the nodes
  hosts: nodes
  roles:
    - role: metrics


Variables in vars.yaml
======================

- `metrics_collector`: The metrics collector to use for the metrics collection. Defaults to `pcp`. Optional values: `"pcp"`, `"collectd"`, `"prometheus"`.
- `metrics_enabled` : When 'True' metrics role will deploy specified configuration file set. Default to 'True'.
- `metrics_purge_confs`: By default, the PCP configuration files are applied on top of pre-existing configuration files. To purge local files prior to setting new ones, set metrics_purge_confs variable to 'True', it will move all configuration files to a backup directory, before deploying the new configuration files. Defaults to 'False'.


- `metrics_elasticsearch_default_ca_cert_path`: Default path to CA cert for ElasticSearch if Elasticsearch installation share the same CA cert. **Note:** If provided, no need to add the `ca_cert` variable in the Elasticsearch output record.
- `metrics_elasticsearch_default_client_cert_path`: Default path to client cert for ElasticSearch if Elasticsearch installation share the same client cert. **Note:** If provided, no need to add the `cert` variable in the Elasticsearch output record.
- `metrics_elasticsearch_default_client_key_path`: Default path to client key for ElasticSearch if Elasticsearch installation share the same client key. **Note:** If provided, no need to add the `key` variable in the Elasticsearch output record.
- `metrics_output_list`: A set of following variables to specify output configurations.  It could be an list if multiple outputs that should to be configured.
   -  **If `type: elasticsearch`** Send metrics to one or more remote elasticsearch or Viaq installations.
      - `name`: Name of the elasticsearch element.
      - `type`: Type of the output element. Optional values: `elasticsearch`, `local`, `custom_files`.
      - `metrics_collections` : List of optional metrics collections that can be configured. [ 'ovirt' ] is predefined.
      - `server_host`: Hostname elasticsearch is running on.
      - `server_port`: Port number elasticsearch is listening to.
      - `index_prefix`: Elasticsearch index prefix the particular log will be indexed to.
      - `ca_cert`: Path to CA cert for ElasticSearch.  Default to '/etc/pcp/viaq/es-ca.crt'
      - `cert`: Path to cert for ElasticSearch.  Default to '/etc/pcp/viaq/es-cert.pem'
      - `key`: Path to key for ElasticSearch.  Default to "/etc/pcp/viaq/es-key.pem"
   -  **If `type: local`** Store metrucs collections locally.
      - `name`: Name of the local output element.
      - `type`: Type of the output element.
      - `metrics_collections` : List of optional metrics collections that can be configured.
   -  **If `type: custom`** To include existing config files in the new ansible deployment, add the paths to custom_config_files as follows.  The specified files are copied to /etc/pcp.
      - `name`: Name of the custom file output element.
      - `type`: Type of the output element.
      - `custom_config_files`: List of custom configuration files. [ '/path/to/custom_A.conf', '/path/to/custom_B.conf' ]. Default to none.



You don't need to update the vars.yaml file if you wish to deploy default PCP configurations.


Additional Resources
--------------------

Additional Collectd, PCP and other custom parameters can be added to the metrics role vars.yaml file,
based on the parameters in the sub-roles README files under the /roles directory.



License
-------

Apache License 2.0

