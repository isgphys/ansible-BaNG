ansible-bang
============

[Ansible](https://www.ansible.com) playbooks to install and configure [BaNG](https://github.com/patschbo/BaNG).

Groups
------

  * bang: BaNG backup servers
  * bangweb: BaNG web frontend and database server
  * bangclient: BaNG backup clients

Configuration
-------------

Adapt the following to your needs:

  * `hosts`
  * `group_vars/all.yml`
  * `group_vars/bangweb.yml`

Vagrant
-------

You can install BaNG in a virtual machine using [Vagrant](https://www.vagrantup.com) and [VirtualBox](https://www.virtualbox.org) with a single command:

```sh
vagrant up
```

The ansible playbooks can be re-run anytime using:

```sh
vagrant provision --provision-with ansible
```

Ansible
-------

Use the dry-run mode to see what changes would be made on the machines defined in the `hosts` file.

```sh
ansible-playbook -C -D site.yml
```

The changes can be pushed to production with:

```sh
ansible-playbook site.yml
```
