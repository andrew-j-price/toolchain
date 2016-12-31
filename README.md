# toolchain

Into DevOps?  Or just being productive?  This is my go to playbook to configure the base tools I need.

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
    - AWS Client
    - Development Tools
    - Docker
    - OpenStack Clients
    - Packer
    - Terraform
  - Grabs
    - Favorite git repos
    - Vagrant boxes

### SSH Keys
If you do leverage this playbook, edit the files below and use your own public keys.  Mine won't help you much.  :)
- authorized_keys
- roles/configure/files/public_keys/default
- roles/configure/files/public_keys/personal
