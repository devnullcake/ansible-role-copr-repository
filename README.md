# Ansible Role: Copr Repository Management
This role allows for the addition and removal of a copr repository from CentOS/Fedora hosts.

### Sample playbook
```yaml
---
- hosts: all
  become: yes
  roles:
    - copr-repository
```

### Standalone usage
```sh
# install repository
ansible-playbook -i inventory -e copr_repository=abn/repository -e copr_repository_action=install copr-repository.yml 

# remove repository
ansible-playbook -i inventory -e copr_repository=abn/repository -e copr_repository_action=remove copr-repository.yml
```

### Dependency usage (meta/main.yml)
```yaml
---
dependencies:
    - { role: copr-repository, copr_repository: "abn/repository", copr_repository_action: "install" }
```
