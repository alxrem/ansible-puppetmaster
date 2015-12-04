[![Ansible Galaxy](https://img.shields.io/ansible/role/5634.svg)](https://galaxy.ansible.com/detail#/role/5634)

puppetmaster
============

Role installs and configures puppetmaster, unicorn and nginx.

Role tested on debian/jessie.

Installs latest puppetmaster 3.x from the Puppetlabs repository.

Replaces `/etc/defaults/unicorn` file. Saves logs of unicorn
at `/var/log/puppet`.

Creates nginx virtual server on port 8140. Stores configuration in
`sites-enabled/puppetmaster`.

Defaults
--------

```yaml
puppetmaster_server_name: puppet
puppetmaster_use_puppetdb: false
unicorn_worker_processes: 2
unicorn_timeout: 30
```
`puppetmaster_server_name` is used as the name of CA.

Dependencies
------------

- alxrem.puppetlabs-release

Example Playbooks
-----------------

Role uses facts, so don't disable `gather_facts`.

If you want to configure puppet to use puppetdb installed on the same host,
include puppetdb role after puppetmaster role.

```yaml
---
- hosts: puppet.example.org
  gather_facts: true
  vars:
    puppetmaster_server_name: puppet.example.org
    unicorn_worker_processes: 8
  roles:
  - alxrem.puppetmaster
```

```yaml
---
- hosts: puppet.example.org
  gather_facts: true
  vars:
    puppetmaster_server_name: puppet.example.org
    puppetmaster_use_puppetdb: true
  roles:
  - alxrem.puppetmaster
  - alxrem.puppetdb
```

License
-------

GPL-3+
