Ansible: Opencast PostgreSQL Role
=================================

[![lint](https://github.com/elan-ev/opencast_postgresql/actions/workflows/lint.yml/badge.svg?branch=main)](https://github.com/elan-ev/opencast_postgresql/actions/workflows/lint.yml?branch=main)
[![molecule](https://github.com/elan-ev/opencast_postgresql/actions/workflows/molecule.yml/badge.svg?branch=main)](https://github.com/elan-ev/opencast_postgresql/actions/workflows/molecule.yml?branch=main)

This Ansible role installs a PostgreSQL database server.


Dependencies
------------

This role requires the PostgreSQL Ansible community collection:

```
ansible-galaxy collection install community.postgresql
```


Role Variables
--------------

- `opencast_postgresql_version`
	- PostgreSQL major version to install (default: `16`)
	- Enables CentOS AppStream
- `opencast_postgresql_user:`
	- Database user to create (default: `opencast`)
- `opencast_postgresql_password`
	- Databse password for user (_required_)
- `opencast_postgresql_database`
	- Database name (default: `opencast`)
- `opencast_postgresql_connection_hosts`
	- List of hosts allowed to connect to database (default: `[127.0.0.1/32, ::1/128]`)


Example Playbook
----------------

Example of how to configure and use the role:

```yaml
- hosts: servers
  become: true
  roles:
    - role: elan.opencast_postgresql
      opencast_postgresql_password: secret
```
