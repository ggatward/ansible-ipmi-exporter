# Ansible Role: ipmi_exporter

## Description

Deploy prometheus [ipmi_exporter](https://github.com/terrycain/ipmi_exporter) using ansible.

## Requirements

- Ansible >= 2.9 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `ipmi_exporter_version` | 0.9.0 | ipmi_exporter package version |
| `ipmi_exporter_web_listen_address` | "0.0.0.0:9496" | Address on which ipmi_exporter will listen |
| `ipmi_exporter_scrape_uri` | https://localhost/ovirt-engine/api/ | Address of the oVirt engine API |
| `ipmi_exporter_ssl_verify` | true | Verify oVirt engine SSL certificate |
| `ipmi_exporter_user` | admin@internal | User to access oVirt engine API |
| `ipmi_exporter_password` | 'ChangeMe' | Password of the user accessing oVirt engine API |
| `ipmi_exporter_password_file` | '' | Location of file containing Password of the user accessing oVirt engine API (optional) |
| `ipmi_exporter_include_disks` | true | Include Storage Domain metrics |
| `ipmi_exporter_include_network` | true | Include Network metrics |
| `ipmi_exporter_include_snapshots` | true | Include Snapshot metrics |
| `ipmi_exporter_config_flags_extra` | {} | Additional configuration flags passed at startup to ipmi_exporter binary |


## Example

### Playbook

Use it in a playbook as follows:
```yaml
- hosts: all
  roles:
    - ipmi_exporter
  vars:
    ipmi_exporter_scrape_uri: https://ovirt-engine.example.com/ovirt-engine/api/
    ipmi_exporter_user: 'prometheus@internal'
    ipmi_exporter_password_file: /root/ovirt_password
```
