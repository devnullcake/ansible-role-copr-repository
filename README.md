COPR Repository Configuration
=============================
[![Build Status](https://travis-ci.org/devnullcake/ansible-role-copr-repository.svg?branch=master)](https://travis-ci.org/devnullcake/ansible-role-acme-certificate) [![Ansible Role](https://img.shields.io/ansible/role/24945.svg)](https://galaxy.ansible.com/devnullcake/acme-certificate/)

This role allows for the addition and removal of a [copr](https://copr.fedorainfracloud.org/) repository from CentOS/Fedora hosts. This implementation is based on instructions provided [here](https://docs.pagure.org/copr.copr/how_to_enable_repo.html#how-to-enable-repo).

Requirements
------------

No additional requirements are enforced other than an a working Ansbile 2.0+ installation.

Role Variables
--------------

A list of available internal configuration variables can be found in the [defaults/main.yml](defaults/main.yml) file.

For simple use cases only `copr_repository` is required. See example playbook for more information.

Dependencies
------------

No Dependencies required other than Ansible itself is expected.

Example Playbook
----------------

    ---
    - name: install abn-keycloak repository on the control host
      hosts: 127.0.0.1
      connection: local
      become: yes
      tasks:
        - include_role:
             name: devnullcake.copr-repository
          vars:
            copr_repository: "abn/keycloak"
            copr_repository_action: "install"

Testing
-------
There are no automated tests defined for this role at the moment. Molecule tests will be added at a later date. Current `tox` execution validates source using [ansible-lint](https://github.com/willthames/ansible-lint).

### Tox
This project has [tox](http://tox.readthedocs.io/en/latest/) configured to run against a clean environment. This can simply be run using tox.

```sh
tox
```

License
-------

Apache License 2.0
