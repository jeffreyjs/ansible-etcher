# Ansible Role: etcher

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This role installs [balenaEtcher](https://github.com/balena-io/etcher) via the debian package from GitHub releases.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

GitHub URL for balneaEtch

```yaml
balena_base_url: https://github.com/{{ etcher_repo }}/releases/download/v{{ etcher_version }}
```

Set the system architecture version

```yaml
etcher_arch: "{% if ansible_architecture == 'x86_64' %}amd64{% else %}{{ ansible_architecture }}{% endif %}"
```

Base name of the GitHub org an repo

```yaml
etcher_repo: balena-io/etcher
```

Set the version to install, if omitted then it will query the GitHub api for the latest release

```yaml
# etcher_version: 1.19.25
```

A file with the current installed version, this is a workaround for checking via a command.

```yaml
etcher_version_file: /usr/share/etcher-version
```

Full URL for the package

```yaml
etcher_url: "{{ balena_base_url }}/{{ __etcher_package }}"
```

Set to present to install, absent to remove

```yaml
etcher_state: present
```

## Dependencies

None.

## Example Playbook

The following is an example of how to use this role:

```yaml
- hosts: server
  roles:
    - role: jeffreyjs.etcher
```

## License

MIT / BSD

## Author Information

[Jeffrey Swindel](https://github.com/jeffreyjs)
