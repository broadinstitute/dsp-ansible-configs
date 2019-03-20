# dsp-ansible-configs

## Overview
This repo is intended to contain all ansible-pull configs. Root level of this repo will contain the various site yamls and the inventory directories will include all group/host vars.

## Provisioner.yml
#### Overview
Provisioner will be called by a metadata script that and will only run once, it take the base role `ansible-role-clone-repos` and clones all repos in `/roles/requirements.yml` this is not the final way to clone repos but it works for now. [ansible-pull-configure](https://github.com/broadinstitute/ansible-pull-configure) is cloned and ran this will configure the ansible-pull cron job, logs and kick off an initial checkin.

**ansible-role-clone-repos should alway be ran as an ```import_role``` so it can clone all the repos before the playbook is compiled otherwise all proceeding roles will fail. ```import_role``` is precompile and ```include_role``` is post compile**
```
---
- hosts: localhost
  tasks:
  - import_role:
      name: ansible-role-clone-repos
  - include_role:
      name: ansible-pull-configure
    vars:
      branch: master
```

### inventories
The inventory structure chosen for this is the [alternative directory layout](https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html#alternative-directory-layout). Each Google project will have it's own inventory/directory, shown below is broad-dsp-techops-dev. For testing purposes this will updated later.
```inventories/
└── broad-dsp-techops-dev
    ├── group_vars
    │   └── docker.yml
    ├── host_vars
    │   └── dsp-mark-dev101.yml
    └── hosts
```

#### Assumptions
- ansible binaries: `/usr/local/bin/ansible/bin/`
- Cloned working directory: `/var/lib/ansible/local`
- inventory path: `/var/lib/ansible/local/inventories/{{ gproject }}/hosts`
- playbook (google project name): `some_google_project_name.yml`
- `<role-name>/meta/main.yml` is needed if using ansible-galaxy in the [ansible-role-clone-repos](https://github.com/broadinstitute/DSP-ansible-configs/tree/master/roles/ansible-role-clone-repos)
