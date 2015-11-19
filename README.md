# Ansible Playbooks for Federated AAI

A collection of playbooks for setting up a hub-and-spoke infrastracture for federated authentication & authorisation. 

## Prerequisites

On the deployment machine (Debian):
* python
* python-apt
* aptitude
* sudo (unless the default ansible `become_method` is overriden or you connect as root)

## Configuration

* Set the target machine hostnames or IP addresses in `development`
* DO change the default simpleSAMLphp admin password in `group_vars/proxyservers`
* Modify variables in `group_vars/proxyservers` to generate the metadata of the SP proxy 

## Action!

Currently, the master playbook (`site.yml`) supports setting up the proxy element(s) of the hub-and-spoke federation based on [simpleSAMLphp](https://simplesamlphp.org).

Assuming bob is a sudoer on the target machines, run:

    ansible-playbook -i development -u bob --ask-become-pass site.yml

Alternatively, if bob prefers to `su` to root then run:

    ansible-playbook -u bob --become-method=su --ask-become-pass -i development site.yml

Finally, if you prefer to connect as root:

    ansible-playbook -u root -i development site.yml
