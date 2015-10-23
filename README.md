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
unicorn_worker_processes: 2
unicorn_timeout: 30
```
`puppetmaster_server_name` is used as the name of CA.

Dependencies
------------

- alxrem.puppetlabs-release

Example Playbook
----------------

Role uses facts, so don't disable `gather_facts`.

```yaml
---
- hosts: puppet.example.org
  gather_facts: true
  vars:
    puppetmaster_server_name: puppet.example.org
    unicorn_worker_processes: 8
  roles:
  - puppetmaster
```

License
-------

GPL-3+
