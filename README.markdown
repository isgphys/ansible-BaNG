ansible-bang
============

Ansible playbook to configure BaNG.

Groups
------

  * bang: BaNG backup servers
  * bangweb: BaNG web frontend
  * bangclient: BaNG backup clients

Configuration
-------------

Adapt the following to your needs:

  * `hosts`
  * `group_vars/all.yml`

Ansible
-------

Dryrun

```sh
ansible-playbook -C -D site.yml
```

Push config

```sh
ansible-playbook site.yml
```
