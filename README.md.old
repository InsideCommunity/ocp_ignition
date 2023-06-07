[![Licence](https://img.shields.io/badge/license-GPL-green?style=flat-square)](./LICENSE)

[![Galaxy](https://camo.githubusercontent.com/51bc3d335aadf1e3345d50486b52228203edb79191bc116300b69923c9455fbc/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f616e7369626c652d67616c6178792d626c61636b2e7376673f7374796c653d666c61742d737175617265266c6f676f3d616e7369626c65)](/https://galaxy.ansible.com/mstrohl)


# ocp_ignition

## Description

Ansible role to generate Openshift Ignition files

# Usage

Overwrite vars defined in defaults to fit your needs.

Create playbook:

```
cat << EOF >> playbook.yml
---
- name: Execute ocp_ignition role
  hosts: localhost
  become: true
  roles:
    - role: ocp_ignition
EOF
```

Execute:

```
ansible-playbook -i inventory playbook.yml
```