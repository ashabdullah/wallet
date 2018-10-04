[![Build Status](https://travis-ci.org/wahidsadik/ansible-role-apache.svg?branch=master)](https://travis-ci.org/wahidsadik/ansible-role-apache)
[![Galaxy](https://img.shields.io/badge/galaxy-ansible--role--apache-green.svg)](https://galaxy.ansible.com/wahidsadik/ansible-role-apache)

Role Name
=========

An Ansible role to install Apache with basic hardening.

The role does these:

- Install apache2
- Change user/group ownership of www-root-location to a non-root user.

The role is available on Ansible Galaxy: [https://galaxy.ansible.com/wahidsadik/ansible-apache-role](https://galaxy.ansible.com/wahidsadik/ansible-role-apache).

To add this role from Ansible Galaxy, run: `ansible-galaxy install wahidsadik.ansible-role-apache`.

To add this from your Ansible `requirements.yml`, add this to the file:

    src: wahidsadik.ansible-role-apache


Requirements
------------

None

Role Variables
--------------

The role defines the following variables in `defaults/main.yml`:

Variable name|Default value|Comment
-------------|-------------|-------
`www_root` | `/var/www` |-
`www_user` | `deployer` | -
`www_group` | `www-data` | -

>Notes:
>
> - `www_user` **must belong** to `www_group` group.
> - `www_user` **should not be** `root` user for security reasons.

Users must pass the following parameters (i.e. variables):

- None

Dependencies
------------

The `remote_user` needs to have `sudo` access or be `root` equivalent user.

Example Playbook
----------------

Example 1: Simplest example with minimum variable passing

    - hosts: servers
      remote_user: root
      roles:
         - wahidsadik.ansible-role-apache

Example 2: With sudo and minimum variable passing

    - hosts: servers
      remote_user: deployer
      become: true
      become_method: sudo
      roles:
      - wahidsadik.ansible-role-apache

Example 3: Overriding additional variables

    - hosts: servers
      remote_user: deployer
      become: true
      become_method: sudo
      roles:
      - {
          role: wahidsadik.ansible-role-apache,
          www_root: /var/web,
          www_user: myuser,
          www_group: www
        }

License
-------

MIT

Author Information
------------------

Wahid Sadik. More at: [https://wahidsadik.github.io](https://wahidsadik.github.io).
