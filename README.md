COPR Repository Configuration
=============================
[![Build Status](https://travis-ci.org/devnullcake/ansible-role-copr-repository.svg?branch=master)](https://travis-ci.org/devnullcake/ansible-role-acme-certificate) [![Ansible Role](https://img.shields.io/ansible/role/25253.svg)](https://galaxy.ansible.com/devnullcake/acme-certificate/)

This role allows for the addition and removal of a [copr](https://copr.fedorainfracloud.org/) repository from CentOS/Fedora hosts. This implementation is based on instructions provided [here](https://docs.pagure.org/copr.copr/how_to_enable_repo.html#how-to-enable-repo).

Requirements
------------

No additional requirements are enforced other than an a working Ansbile 2.4+ installation.

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
Before testing, you need to ensure that the submodules required have been cloned.
```sh
git submodule update --init --recursive
```

### Local Environment
This role uses [Molecule](https://molecule.readthedocs.io/en/latest/) and docker instances to enable testing. You can run this locally on your development environment provided you have python installed and are running the docker daemon.

```sh
# install molecule and docker-py requirements
pip install -r test-requirements.txt
molecule test
```

This will as configured in the default molecule scenario, spin up containers of the supported distributions and execute a sample playbook.

### Tox
This project also has [tox](http://tox.readthedocs.io/en/latest/) configured to run against multiple ansible versions with [Molecule](https://molecule.readthedocs.io/en/latest/). This can simply be run using tox.

```sh
tox
```

Refer to the [Molecule documentation](https://molecule.readthedocs.io/en/latest/testing.html) and [tox documentation](http://tox.readthedocs.io/en/latest/) for advance usage instructions.

License
-------

Apache License 2.0
