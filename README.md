# Role for Zsh setup

[![CI](https://github.com/unleftie/ansible-role-zsh/actions/workflows/ci.yml/badge.svg)](https://github.com/unleftie/ansible-role-zsh/actions/workflows/ci.yml)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/unleftie/ansible-role-zsh/badge)](https://securityscorecards.dev/viewer/?uri=github.com/unleftie/ansible-role-zsh)

## Compatibility

| Platform | Version |
| -------- | ------- |
| debian   | 12      |

## Dependencies

- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) (v2.14+)
- [Molecule](https://molecule.readthedocs.io/en/latest/installation.html) + (v4.0.4+) + [docker plugin](https://github.com/ansible-community/molecule-plugins) (for local testing)
- [Docker](https://docs.docker.com/get-docker/) (for local testing)

## Local Testing

```sh
git clone https://github.com/unleftie/ansible-role-zsh.git
cd ansible-role-zsh/
molecule test
```

## Installation

> Upgradability notice: When upgrading from old version of this role, be aware that some files may be lost.

To deploy the Zsh on hosts, add the Datadog role to your playbook. Below are some sample playbooks to assist you with using the Zsh Ansible role.

```yml
- name: Sample 1
  hosts: all
  become: true
  pre_tasks:
    - name: Ensure apt cache are updated
      apt:
        update_cache: true
        cache_valid_time: 3600
      when: ansible_os_family == "Debian"
  tasks:
    - include_role:
        name: "ansible-role-zsh"
```

## Variables

| Variable               | Description                                | Values                         |
| ---------------------- | ------------------------------------------ | ------------------------------ |
| `zsh_default_theme`    | Default theme name                         |
| `zsh_update_mode`      | Update mode                                | "disabled", "auto", "reminder" |
| `zsh_update_frequency` | Update frequency                           | 0-x (days)                     |
| `zsh_locale`           | System locale value                        |
| `zsh_config_path`      | Path to place config file for user account |

## 📝 License

This project is licensed under the [MIT](LICENSE).
