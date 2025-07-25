Changelog
=========

[1.13.0] - 2025-07-24
--------------------

### New Features

- feat: add metrics_optional_domains and metrics_optional_packages for users to configure optional domains (#245)

### Bug Fixes

- fix: add missing Spark import/export support for metrics - part 2 (#246)

[1.12.0] - 2025-07-02
--------------------

### New Features

- feat: Support this role in container builds (#243)

### Other Changes

- ci: bump tox-lsr to 3.8.0; rename qemu/kvm tests (#238)
- ci: Add Fedora 42; use tox-lsr 3.9.0; use lsr-report-errors for qemu tests (#239)
- ci: Add support for bootc end-to-end validation tests (#240)
- ci: Use ansible 2.19 for fedora 42 testing; support python 3.13 (#241)

[1.11.0] - 2025-05-06
--------------------

### New Features

- feat: add missing Spark import/export support for metrics (#233)

### Other Changes

- ci: ansible-plugin-scan is disabled for now (#224)
- ci: bump ansible-lint to v25; provide collection requirements for ansible-lint (#227)
- ci: Check spelling with codespell (#228)
- ci: Add test plan that runs CI tests and customize it for each role (#229)
- ci: In test plans, prefix all relate variables with SR_ (#230)
- ci: Fix bug with ARTIFACTS_URL after prefixing with SR_ (#231)
- ci: several changes related to new qemu test, ansible-lint, python versions, ubuntu versions (#232)
- ci: use tox-lsr 3.6.0; improve qemu test logging (#234)
- ci: skip storage scsi, nvme tests in github qemu ci (#235)
- ci: bump sclorg/testing-farm-as-github-action from 3 to 4 (#236)

[1.10.9] - 2025-01-09
--------------------

### Other Changes

- ci: Use Fedora 41, drop Fedora 39 (#221)
- ci: Use Fedora 41, drop Fedora 39 - part two (#222)

[1.10.8] - 2024-11-19
--------------------

### Bug Fixes

- fix: use __grafana_keyserver_datasource_type variable instead of its string value
- fix: Use correct syntax for keyserver port and test check

[1.10.7] - 2024-10-30
--------------------

### Bug Fixes

- fix: add support for Valkey (#212)
- fix: add leading triple-hyphen to all github workflow files (#214)

### Other Changes

- docs: fix missing h2 markdown element (#211)
- ci: Add tags to TF workflow, allow more [citest bad] formats (#213)
- ci: ansible-test action now requires ansible-core version (#215)
- refactor: Use vars/RedHat_N.yml symlink for CentOS, Rocky, Alma wherever possible (#217)

[1.10.6] - 2024-08-19
--------------------

### Other Changes

- ci: Add tft plan and workflow (#203)
- ci: Update fmf plan to add a separate job to prepare managed nodes (#205)
- ci: bump sclorg/testing-farm-as-github-action from 2 to 3 (#206)
- ci: Add workflow for ci_test bad, use remote fmf plan (#207)
- ci: Fix missing slash in ARTIFACTS_URL (#208)
- test: stop firewall if used by test (#209)

[1.10.5] - 2024-07-23
--------------------

### Bug Fixes

- fix: Handle undefined item in pmie configuration

[1.10.4] - 2024-07-15
--------------------

### Bug Fixes

- fix: add configuration files for c10s and el10 (#199)
- fix: add support for EL10 (#200)

### Other Changes

- ci: ansible-lint action now requires absolute directory (#198)

[1.10.3] - 2024-06-11
--------------------

### Other Changes

- ci: use tox-lsr 3.3.0 which uses ansible-test 2.17 (#193)
- ci: tox-lsr 3.4.0 - fix py27 tests; move other checks to py310 (#195)
- ci: Add supported_ansible_also to .ansible-lint (#196)

[1.10.2] - 2024-04-04
--------------------

### Other Changes

- ci: fix python unit test - copy pytest config to tests/unit (#188)
- ci: bump ansible/ansible-lint from 6 to 24 (#189)
- ci: make markdownlint ignore tests/roles (#190)
- ci: bump mathieudutour/github-tag-action from 6.1 to 6.2 (#191)

[1.10.1] - 2024-01-16
--------------------

### Other Changes

- ci: Use supported ansible-lint action; run ansible-lint against the collection (#186)

[1.10.0] - 2023-12-12
--------------------

### New Features

- feat: sync with latest ansible-pcp (#178)
- feat: support for ostree systems

### Bug Fixes

- fix: add missing pmie webhook action configuration functionality (#183)

### Other Changes

- refactor: improve support for ostree systems (#179)
- ci: bump actions/github-script from 6 to 7 (#180)
- refactor: get_ostree_data.sh use env shebang - remove from .sanity* (#182)

[1.9.0] - 2023-11-06
--------------------

### New Features

- feat: support for ostree systems (#175)

### Other Changes

- build(deps): bump actions/checkout from 3 to 4 (#167)
- ci: dependabot commit msg lint; sort badges (#170)
- ci: use dump_packages.py callback to get packages used by role (#172)
- ci: tox-lsr version 3.1.1 (#174)

[1.8.7] - 2023-09-08
--------------------

### Other Changes

- ci: Add markdownlint, test_converting_readme, and build_docs workflows (#163)

  - markdownlint runs against README.md to avoid any issues with
    converting it to HTML
  - test_converting_readme converts README.md > HTML and uploads this test
    artifact to ensure that conversion works fine
  - build_docs converts README.md > HTML and pushes the result to the
    docs branch to publish dosc to GitHub pages site.
  - Fix markdown issues in README.md
  
  Signed-off-by: Sergei Petrosian <spetrosi@redhat.com>

- docs: Make badges consistent, run markdownlint on all .md files (#164)

  - Consistently generate badges for GH workflows in README RHELPLAN-146921
  - Run markdownlint on all .md files
  - Add custom-woke-action if not used already
  - Rename woke action to Woke for a pretty badge
  
  Signed-off-by: Sergei Petrosian <spetrosi@redhat.com>

- ci: Remove badges from README.md prior to converting to HTML (#165)

  - Remove thematic break after badges
  - Remove badges from README.md prior to converting to HTML
  
  Signed-off-by: Sergei Petrosian <spetrosi@redhat.com>

[1.8.6] - 2023-07-19
--------------------

### Other Changes

- ci: Add pull request template and run commitlint on PR title only (#159)
- ci: Rename commitlint to PR title Lint, echo PR titles from env var (#160)
- ci: ansible-lint - ignore var-naming[no-role-prefix] (#161)

[1.8.5] - 2023-05-26
--------------------

### Bug Fixes

- fix: make role work on ansible-core 2.15

### Other Changes

- docs: Consistent contributing.md for all roles - allow role specific contributing.md section
- docs: remove unused Dependencies section in README

[1.8.4] - 2023-04-27
--------------------

### Other Changes

- test: check headers for ansible_managed, fingerprint
- ci: Add commitlint GitHub action to ensure conventional commits with feedback

[1.8.3] - 2023-04-14
--------------------

### Other Changes

- fix additional ansible-lint issues

[1.8.2] - 2023-04-06
--------------------

### Other Changes

- Add README-ansible.md to refer Ansible intro page on linux-system-roles.github.io (#146)
- Fingerprint ansible-pcp managed config files

[1.8.1] - 2023-01-20
--------------------

### New Features

- none

### Bug Fixes

- fix pimeconf rule filesys vfs_rules support
- ansible-lint 6.x fixes (#133)

### Other Changes

- Add check for non-inclusive language
- Avoid non-inclusive language

[1.8.0] - 2022-11-01
--------------------

### New Features

- Use the firewall role and the selinux role from the metrics role

- Introduce metrics_manage_firewall to use the firewall role to
  manage the pmcd, pmproxy, grafana and valkey or redis ports,
  depending on the configuration parameters.
  metrics_manage_firewall is set to false, by default.

- Introduce metrics_manage_selinux to use the selinux role to
  manage the pmcd, pmproxy, grafana and valkey or redis ports,
  depending on the configuration parameters.
  metrics_manage_selinux is set to false, by default.

- Add the test check task check_firewall_selinux.yml for verify
  the ports status.

- Skip calling the firewall role when the managed node is rhel-6.

- When metrics_manage_firewall and metrics_manage_selinux are set
  to false, the firewall role and the selinux role are not used,
  respectively.

### Bug Fixes

- grafana: small wording tweak to grafana v8/v9 action names
- grafana: include config file for Grafana v9
- grafana: update grafana.ini to permit all grafana-pcp plugin components

### Other Changes

- none

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
- update to tox-lsr 2.4.0 - add support for ansible-test with docker
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
- tests\_sanity\_into\_elasticsearch fails - \_\_elasticsearch\_packages\_export\_pcp is undefined <!--- wokeignore:rule=sanity -->
- tests\_sanity\_bpftrace failure in task Check if allowed users of bpftrace are configured <!--- wokeignore:rule=sanity -->
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
