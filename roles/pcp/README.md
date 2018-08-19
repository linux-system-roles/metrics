## Performance Co-Pilot

This role runs the dependent pcp roles, the Roles list is located in the meta directory.

It is run as part of the `Configure Metrics` play and the default `configure` tag.

The available variables for this role are:

- `pcp_service_name:` (default `"pcp"`)

   PCP service name.

- `pcp_pmcd_service_name:` (default `"pmcd"`)

   PMCD service name.

- `pmlogger_service_name:` (default `"pmlogger"`)

   PMLOGGER service name.

- `pmie_service_name:` (default `"pmie"`)

   PMIE service name.

- `pmmgr_service_name:` (default `"pmmgr"`)

   PMMGR service name.

- `pmwebd_service_name:` (default `"pmwebd"`)

   PMWEBD service name.

