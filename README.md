# Ansible Playbooks for Federated AAI

## Prerequisites

On the deployment machine (Debian):
* python
* python-apt
* aptitude
* sudo (unless the default ansible `become_method` is overriden or you connect as root)

## Configuration

* Set the target machine hostnames or IP addresses in `development`
* DO change the default simpleSAMLphp admin password in `group_vars/sspservers`

## Action!

Assuming bob is a sudoer on the target machines, run `ansible-playbook -i development -u bob --ask-become-pass site.yml`

Alternatively, if bob prefers to `su` to root then run `ansible-playbook -u bob --become-method=su --ask-become-pass -i development site.yml`
