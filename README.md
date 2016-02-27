# toolchain

Into Devops?  Or just being productive?  This is my go to playbook to configure the base tools I need on a dev/lab instance.

### Cross Platform
Playbook runs against:
  - CentOS/RHEL
  - Fedora
  - Ubuntu

### In the Box
The toolchain is easily expandable, but here are some of the basics for what it provides to get you running quickly.
  - Configures
    - Ansible
    - Docker
    - OpenStack Clients
    - Vagrant
  - Grabs
    - Favorite git repos
    - Vagrant boxes

### Quick Start Guide
  - Clone repo
  - Edit ./roles/play/files/public_keys/default
  - Run "vagrant up"
