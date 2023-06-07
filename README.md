# insidegroup.ocp_ignition

[![Maintainer](https://img.shields.io/badge/maintained%20by-InsideCommunity-00548c?style=flat-square)](https://github.com/InsideCommunity)
[![License](https://img.shields.io/github/license/InsideCommunity/ocp_ignition?style=flat-square)](https://github.com/InsideCommunity/ocp_ignition/blob/main/LICENSE)
[![Release](https://img.shields.io/github/v/release/InsideCommunity/ocp_ignition?style=flat-square)](https://github.com/InsideCommunity/ocp_ignition/releases)
[![Status](https://img.shields.io/github/workflow/status/InsideCommunity/ocp_ignition/Ansible%20Molecule?style=flat-square&label=tests)](https://github.com/InsideCommunity/ocp_ignition/actions?query=workflow%3A%22Ansible+Molecule%22)
[![Ansible Galaxy](https://img.shields.io/badge/ansible-galaxy-black.svg?style=flat-square&logo=ansible)](https://galaxy.ansible.com/insidegroup/ocp_ignition)[![Ansible version](https://img.shields.io/badge/ansible-%3E%3D2.9-black.svg?style=flat-square&logo=ansible)](https://github.com/ansible/ansible)

⭐ Star us on GitHub — it motivates us a lot!

Create ignition files to install Red Hat Openshift or OKD

**Platforms Supported**:

| Platform | Versions |
|----------|----------|
| Ubuntu | focal, jammy |
| Fedora | all |

## ⚠️ Requirements

Ansible >= 2.9.

### Ansible role dependencies

None.

## ⚡ Installation

### Install with Ansible Galaxy

```shell
ansible-galaxy install insidegroup.ocp_ignition
```

### Install with git

If you do not want a global installation, clone it into your `roles_path`.

```bash
git clone https://github.com/InsideCommunity/ocp_ignition.git  insidegroup.ocp_ignition
```

But I often add it as a submodule in a given `playbook_dir` repository.

```bash
git submodule add https://github.com/InsideCommunity/ocp_ignition.git roles/insidegroup.ocp_ignition
```

As the role is not managed by Ansible Galaxy, you do not have to specify the
github user account.

### ✏️ Example Playbook

Basic usage is:

```yaml
- hosts: all
  roles:
    - role: insidegroup.ocp_ignition
      vars:
        ocp_ignition_base_domain: example.com
        ocp_ignition_butane_boot_device: {}
        ocp_ignition_butane_disabled: false
        ocp_ignition_butane_passwd: {}
        ocp_ignition_butane_storage:
          files:
            - contents:
                inline: Ansible Generated file from ocp_ignition role provided by InsideGroup(www.insidegroup.fr)
              mode: 420
              path: /etc/ignition_example_file
          filesystems:
            - device: /dev/mapper/root
              format: xfs
              wipe_filesystem: true
          luks:
            - device: /dev/disk/by-partlabel/root
              key_file:
                inline: AZERTyuiop
              name: luks-root
        ocp_ignition_cluster_name: ocp4
        ocp_ignition_config_cluster_networks:
          - cidr: 10.128.0.0/14
            hostPrefix: 23
        ocp_ignition_config_proxy: {}
        ocp_ignition_config_pull_secret: ''
        ocp_ignition_config_service_networks:
          - 172.30.0.0/16
        ocp_ignition_config_ssh_key: ''
        ocp_ignition_config_trust_bundle: ''
        ocp_ignition_dest: /var/www/html/example/ignitions
        ocp_ignition_ocp_version: 4.12.0
        ocp_ignition_private_dest: /home/user/ignitions
        ocp_ignition_role: controler
        ocp_ignition_safe_mode: true
        
```

## ⚙️ Role Variables

Variables are divided in three types.

The **default vars** section shows you which variables you may
override in your ansible inventory. As a matter of fact, all variables should
be defined there for explicitness, ease of documentation as well as overall
role manageability.

The **context variables** are shown in section below hint you
on how runtime context may affects role execution.

### Default variables
Role default variables from `defaults/main.yml`.

| Variable Name | Value |
|---------------|-------|
| ocp_ignition_ocp_version | 4.12.0 |
| ocp_ignition_safe_mode | True |
| ocp_ignition_private_dest | /home/user/ignitions |
| ocp_ignition_dest | /var/www/html/example/ignitions |
| ocp_ignition_role | controler |
| ocp_ignition_cluster_name | ocp4 |
| ocp_ignition_base_domain | example.com |
| ocp_ignition_butane_disabled | False |
| ocp_ignition_butane_storage | [] |
| ocp_ignition_butane_passwd | {}<br> |
| ocp_ignition_butane_boot_device | {}<br> |
| ocp_ignition_config_proxy | {}<br> |
| ocp_ignition_config_trust_bundle |  |
| ocp_ignition_config_cluster_networks | - cidr: 10.128.0.0/14<br>  hostPrefix: 23<br> |
| ocp_ignition_config_service_networks | - 172.30.0.0/16<br> |
| ocp_ignition_config_pull_secret |  |
| ocp_ignition_config_ssh_key |  |

 
Focus on **ocp_ignition_butane_storage** if you needed to customize networking
```yaml
# Should be defined in host_vars or both group_vars and host_vars
ocp_ignition_butane_storage:
files:
- contents:
    inline: Ansible Generated file from ocp_ignition role provided by InsideGroup(www.insidegroup.fr)
  mode: 420
  path: /etc/ignition_example_file
filesystems:
- device: /dev/mapper/root
  format: xfs
  wipe_filesystem: true
luks:
- device: /dev/disk/by-partlabel/root
  key_file:
    inline: AZERTyuiop
  name: luks-root

```
### Context variables

None.

## ©️ [License](LICENSE)

## 📄 [CHANGELOG.md](CHANGELOG.md)

## Author Information

Inside Group

## 👏 Special thanks

README generated with [ansible-gendoc](https://github.com/claranet/ansible-gendoc)