Install Custom Root CA Certificates
=========

This role can be used to install trusted Root CA certificates in Ubuntu
hosts.

[![Build Status](https://github.com/Rheinwerk/ansible-role-install_root_ca_certs/actions/workflows/ci.yml/badge.svg)](https://github.com/Rheinwerk/ansible-role-install_root_ca_certs/actions/workflows/ci.yml)

Requirements
------------

The Root CA certificates to be installed in PEM format.


Role Variables
--------------

There is one main variable that drives this role: `_install_root_ca_certs`. It is a map that contains all configuration and settings for this role.
Please see `defaults/main.yml` for details.

Dependencies
------------

None.


Example Playbook
----------------

The general contract of this role is to take the variables map `_install_root_ca_certs` from `defaults/main.yml` as a template for your configuration and pass that configuration as a parameter to this role.

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      var:
        INSTALL_ROOT_CA_CERTS:
          ...
      roles:
         - { role: install_root_ca_certs, tags: [ 'install_root_ca_certs' ], _install_root_ca_certs: "{{ INSTALL_ROOT_CA_CERTS }}" }

License
-------

Please see LICENSE.

Author Information
------------------

Original author is [Daniel Schneller](https://github.com/dschneller) as member of the [Rheinwerk](https://github.com/Rheinwerk) project.

