Ansible: Opencast PostgreSQL Role
=================================

This Ansible role installs and prepares a PostgreSQL database server for Opencast.


Dependencies
------------

This role requires the PostgreSQL community collection:

```
ansible-galaxy collection install community.postgresql
```


Role Variables
--------------

- `opencast_postgresql_version`
	- PostgreSQL major version to install (default: `12`)
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
