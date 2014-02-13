# Akeneo Ansible playbook

Install Akeneo with every thing it needs:
 - NGinx
 - PHP-FPM
 - PHP 5.5
 - MySQL

If you have some improvement ideas feel free to send us a PR, we will <3 them!

## Installation

First of all you need to [install Ansible](http://docs.ansible.com/intro_installation.html)
on your own machine.
Then clone this repository somewhere:

```bash
$ git clone https://github.com/theodo/akeneo-ansible-provisioning.git
$ cd akeneo-ansible-provisioning
```

## Configuration

First configure the hosts on which you want to install Akeneo in the files
contained in the ```hosts``` directory. Here is a sample ```production``` file:

```ini
[akeneo:children]
production

[production]
akeneo.theodo.fr
```

This configuration will automatically tell to provision the server on
```akeneo.theodo.fr``` if you tell ansible to run the playbook with
```production``` inventory parameter (-i)

By default, the playbook contains every thing you would need. But your can
configure it with your ownvalues. To do so edit the ```playbook/group_vars/all```.

## Running in Vagrant

This playbook provides also a Vagrant file. Simply run ```vagrant up``` and
let Vagrant create, boot and provision the VM. Add the host you configured in
your ```/etc/hosts``` file (akeneo.local by default):

```bash
#/etc/bash
10.0.0.30 akeneo.local
```

Note: vagrant is configured to use the ```hosts/development```  inventory file

Then Akeneo is available on htpp://akeneo.local.

## Running on your server!

You can of course use the playbook without Vagrant! Once you've configured the
playbook to suits your needs, run ansible to configure your server:

```bash
$ ansible-playbook -i production site.yml
```
