## roles are configured in the ansible-clone-repoclone defaults/main.yml
##  By default it will clone all roles but you can specify in group vars to only clone what is needed.
```bash
gitrepos:
#ansiblepull
  - { address: 'https://github.com/broadinstitute/ansible-role-configure.git', name: 'ansible-role-configure' }
#docker
  - { address: 'https://github.com/broadinstitute/ansible-role-docker.git', name: 'ansible-role-docker' }
#lvm
  - { address: 'https://github.com/broadinstitute/ansible-role-lvm.git, name: 'ansible-role-lvm' }
#basepacks
  - { address: 'https://github.com/broadinstitute/ansible-role-basepackages.git, name: 'ansible-role-basepackage' }
#lvmthinlpool
  - { address: 'https://github.com/broadinstitute/ansible-role-docker-thinpool.git, name: 'ansible-role-docker-thinpool' }
#stackdriver
  - { address: 'https://github.com/broadinstitute/ansible-role-stackdriver.git, name: 'ansible-role-stackdriver' }
#yumcron
  - { address: 'https://github.com/broadinstitute/ansible-role-yum-cron.git, name: 'ansible-role-yum-cron' }
#sentinelone
  - { address: 'https://github.com/broadinstitute/ansible-role-sentinelone.git, name: 'ansible-role-sentinelone' }

    ```
