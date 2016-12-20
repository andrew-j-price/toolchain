# toolchain

Into DevOps?  Or just being productive?  This is my go to playbook to configure the base tools I need on a dev/lab instance.

### Vagrant Instances
Provision one or all of the following:
  - xubuntu (with Atom IDE)
  - trusty
  - xenial
  - fedora24
  - centos7
  - centos-atomic

### Cross Platform
Playbook runs against:
  - CentOS/RHEL
  - Fedora
  - Ubuntu

### In the Box
The toolchain is easily expandable, but here are some of the basics for what it provides to get you running quickly.
  - Configures
    - Ansible
    - Development Tools
    - Docker
    - OpenStack Clients
  - Grabs
    - Favorite git repos
    - Vagrant boxes

### Quick Start Guide
  - Clone repo
  - Edit authorized_keys
  - Edit roles/configure/files/public_keys/default
  - Run "vagrant up"
