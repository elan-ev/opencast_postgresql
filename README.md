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
- `opencast_postgresql_user`
	- Database user to create (default: `opencast`)
- `opencast_postgresql_password`
	- Databse password for user (_required_)
- `opencast_postgresql_database`
	- Database name (default: `opencast`)
- `opencast_postgresql_listen_addresses`
	- List of IP addresses the server should listen on (default: `["localhost"]`).
	- Use `*` to listen on all IP addresses.
	- For more information please consult PostgreSQL documentation for the configuration `listen_addresses`
- `opencast_postgresql_connection_hosts`
	- List of IP ranges allowed to connect to database (default: `[127.0.0.1/32, ::1/128]`)
- `opencast_postgresql_extra_configs`
	- Additional server configurations as dictionary (default: `{}`)
	- Please consult PostgreSQL documentation for available configurations


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

More complex example with custom configurations and listening on all IP addresses is shown here:

```yaml
- hosts: servers
  become: true
  roles:
    - role: elan.opencast_postgresql
      opencast_postgresql_password: secret
      opencast_postgresql_extra_configs:
        max_connections: 1000        # Increased value for production use
        log_destination: "'syslog'"  # Log to syslog
      opencast_postgresql_listen_addresses:
        - "*"                        # Listen on all IP addresses
      opencast_postgresql_connection_hosts:
        - "127.0.0.1/32"
        - "::1/128"
        - "10.10.10.1/24"            # Clients IP range
```
