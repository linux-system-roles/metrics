Changelog
=========

[1.7.3] - 2022-07-19
--------------------

### New Features

- none

### Bug Fixes

- docs: make minimum redis and grafana versions more clear

Tackles Red Hat BZ #2094483

- restart pmie, pmlogger if changed, do not wait for handler

### Other Changes

- make min_ansible_version a string in meta/main.yml

The Ansible developers say that `min_ansible_version` in meta/main.yml
must be a `string` value like `"2.9"`, not a `float` value like `2.9`.

- Add changelog_to_tag.yml to .github/workflows

- Add CHANGELOG.md

[1.7.2] - 2022-05-10
--------------------

### New Features

- Add CentOS 9 platform variables for each role

### Bug Fixes

- none

### Other Changes

- bump tox-lsr version to 2.11.0; remove py37; add py310

[1.7.1] - 2022-04-28
--------------------

### New Features

- none

### Bug Fixes

- none

### Other Changes

- Update tests with shell/grep cleanups

[1.7.0] - 2022-04-27
--------------------

### New Features

- Add a metrics\_from\_postfix boolean flag for the metrics role

### Bug Fixes

- Resolve race condition with starting pmdapostfix
- Ensure a postfix log file exists for pmdapostfix to start

### Other Changes

- Make all PMDA test checking with pmprobe more resilient
- Update tests using pmprobe to check agents for resilience
- Use correct role variable locations in mssql tests
- Incorporate improved bool test syntax suggestion
- Use correct role variable locations in mssql tests

[1.6.0] - 2022-04-20
--------------------

### New Features

- Provide pcp_\single\_control option for control.d vs control files

### Bug Fixes

- none

### Other Changes

- none

[1.5.1] - 2022-03-14
--------------------

### New Features

- none

### Bug Fixes

- none

### Other Changes

- Add test cases for the ansible\_managed header.

[1.5.0] - 2022-03-02
--------------------

### New Features

- Support metrics from postfix mail servers
- Add "follow: yes" to the template task in the mssql and elasticsearch subrole.

### Bug Fixes

- none

### Other Changes

- Add test cases for the ansible\_managed header.

[1.4.3] - 2022-02-23
--------------------

### New Features

- System Roles should consistently use ansible\_managed in configuration files it manages

### Bug Fixes

- none

### Other Changes

- bump tox-lsr version to 2.10.1

[1.4.2] - 2022-01-20
--------------------

### New Features

- none

### Bug Fixes

- Address PyYAML vulnerability

### Other Changes

- none

[1.4.1] - 2022-01-10
--------------------

### New Features

- Specify grafana username/password

### Bug Fixes

- none

### Other Changes

- bump tox-lsr version to 2.8.3
- Bump version in galaxy.yml
- change recursive role symlink to individual role dir symlinks

[1.4.0] - 2021-12-06
--------------------

### New Features

- none

### Bug Fixes

- none

### Other Changes

- Convert to using git-subtree for ansible-pcp sync-up
- Run the new tox test
- update tox-lsr version to 2.8.0
- Add github action workflow to sync with ansible-pcp nightly
- Add Fedora bpftrace package details for CI

[1.3.3] - 2021-11-08
--------------------

### New Features

- support python 39, ansible-core 2.12, ansible-plugin-scan

### Bug Fixes

- none

### Other Changes

- update tox-lsr version to 2.7.1

[1.3.2] - 2021-09-13
--------------------

### New Features

- none

### Bug Fixes

- none

### Other Changes

- use apt-get install -y
- use tox-lsr version 2.5.1
- check\_redis should use shell not command

[1.3.1] - 2021-08-16
--------------------

### New Features

- none

### Bug Fixes

- bpftrace: follow bpftrace.conf symlink for latest PCP versions

### Other Changes

- none

[1.3.0] - 2021-08-10
--------------------

### New Features

- Raise supported Ansible version to 2.9

### Bug Fixes

- none

### Other Changes

- none

[1.2.3] - 2021-06-02
--------------------

### New Features

- none

### Bug Fixes

- \_\_pcp\_target\_hosts not defined so loop doesn't run

### Other Changes

- none

[1.2.2] - 2021-05-06
--------------------

### New Features

- Add CentOS\_9 variable definitions for all PCP roles

### Bug Fixes

- Fix issues found by linters - enable all tests on all repos - remove suppressions
- Revert accidental inclusion of var path from the spark role
- Partial Revert "RHELPLAN-68122 - Collections - Metrics - fixing ansible-test errors"
- Fix ansible-test errors

### Other Changes

- Remove python-26 environment from tox testing
- update to tox-lsr 2.4.0 - add support for ansible-test sanity with docker
- CI: Add support for RHEL-9

[1.2.1] - 2021-02-22
--------------------

### New Features

- Add platform variables for RHEL 9 to all roles.

### Bug Fixes

- do not use ignore\_errors: yes

### Other Changes

- Update mssql test to exclude non-x86\_64 architectures
- use tox-lsr 2.2.0

[1.2.0] - 2021-02-05
--------------------

### New Features

- Update configuration file paths to support older PCP versions
- Define Fedora specific variables for export into Elasticsearch
- Rename the embedded roles to remove 'performancecopilot' naming
- Make sure elasticsearch\_agent is always defined
- Make sure config dir of PMDAs exist
- Add centos8

### Bug Fixes

- Configuration of bpftrace PMDA does not work on platforms where PCP version is less or equal to 5.1 
- Local role variable "role\_name" conflicts with global variable of the same name
- The role fails on RHEL-6 due to missing "cyrus-sasl-scram" package
- pmrepconf is not available on all platforms
- PMCD is not restarted on RHEL platform
- SASL authentication is not configured properly
- PMCD is not restarted after installation of ElasticSearch agent
- Missing installation of BCC agent when "metrics\_graph\_service: yes" is set
- Missing default value for "elasticsearch\_agent" causes "performancecopilot\_metrics\_elasticsearch" role to fail
- Wrong setup of bpftrace users
- MSSQL agent does not register it self in PMCD due to missing python3-pyodbc package
- Configuration of Elasticsearch, MSSQL and BPFtrace agents fail
- Metrics sub-roles are not visible to Ansible in default configuration
- The role uses wrong role name when pointing to it self
- Typo in README.md - metrics\_with\_elasticsearch to be replaced by metrics\_into\_elasticsearch
- Fix of misspelled "Elasticsearch"
- Corrections to recently added metrics role functionality
- Fix wrong main role name in sub-roles
- Fix centos6 repos; use standard centos images

### Other Changes

- Document the reasons for the use of ignore\_errors
- Implementation of feature/platform support matrix into tests
- Set of tests to support new functionality in the metrics role
- remove ansible 2.7 support from molecule
- use tox-lsr 1.0.2
- use tox for ansible-lint instead of molecule
- use new tox-lsr plugin
- use github actions instead of travis
- tests\_sanity\_into\_elasticsearch fails - \_\_elasticsearch\_packages\_export\_pcp is undefined
- tests\_sanity\_bpftrace failure in task Check if allowed users of bpftrace are configured
- Fix a typo in README file

[1.1.1] - 2020-12-04
--------------------

### New Features

- none

### Bug Fixes

- none

### Other Changes

- Document the ports used for various metrics role configurations

[1.1.0] - 2020-11-11
--------------------

### New Features

- Update fields names collected from the openmetrics endpoint
- Multiple inputs to multiple outputs
- \[PCP\] Add collection from openmetrics end point
- Update metrics role to use roles from the PCP collection

### Bug Fixes

- none

### Other Changes

- meta/main.yml: CI add support for Fedora 33
- lock ansible-lint version at 4.3.5; suppress role name lint warning
- sync collections related changes from template to metrics role

[1.0.0] - 2020-08-24
--------------------

### Initial Release
