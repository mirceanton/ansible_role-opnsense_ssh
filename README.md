OPNsense: SSH
=============

An ansible role to manage the SSH server on an opnSense firewall.

Requirements
------------

This role requires the `lxml` python package to be installed on the host system.

Role Variables
--------------

|          Variable          |  Type  |                   Description                    |
| :------------------------: | :----: | :----------------------------------------------: |
|    opnsense_ssh_status     |  bool  |          Enable/Disable the SSH server.          |
|  opnsense_ssh_interfaces   | string | Comma-separated list of interfaces to listen on. |
|     opnsense_ssh_port      |  int   |      The port number for SSH to listen on.       |
|    opnsense_ssh_groups     | string |  Comma-separated list of groups allowed to SSH.  |
| opnsense_ssh_password_auth |  bool  |     Enable/Disable password authentication.      |
|  opnsense_ssh_permit_root  |  bool  |        Enable/Disable remote root logins.        |
|  opnsense_ssh_permit_sudo  |  bool  |       Enable/Disable privilege escalation.       |
|    opnsense_ssh_noauto     |  bool  |              Enable/Disable noauto               |
|  opnsense_ssh_auto_logout  |  int   |     Interval in minutes before auto logout.      |

Dependencies
------------

N/A.

Example Playbook
----------------

```yaml
- name: Configure SSH on all firewalls
  hosts: opnsense

  roles:
    - role: mirceanton.opnsense_ssh
      vars:
        opnsense_ssh_status: enabled       # enabled / disabled
        opnsense_ssh_interfaces: lan       # comma separated list of interfaces SSH binds to
        opnsense_ssh_port: 22              # SSH port
        opnsense_ssh_groups: admins        # allowed groups for SSH
        opnsense_ssh_password_auth: true   # enable / disable password based authentication
        opnsense_ssh_permit_root: true     # enable / disable root login via SSH
        opnsense_ssh_permit_sudo: true     # enable / disable privilege escalation
        opnsense_ssh_noauto: true          # enable / disable noauto
        opnsense_ssh_auto_logout: 1        # ssh auto logout in minutes
```

License
-------

MIT

Author Information
------------------

A role developed by [Mircea-Pavel ANTON](https://www.mirceanton.com).
