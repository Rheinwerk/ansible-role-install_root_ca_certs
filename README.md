Install Custom Root CA Certificates
=========

This role installs trusted CA certificates into the Debian system trust store
(`/usr/local/share/ca-certificates`, then `update-ca-certificates`).

[![Build Status](https://github.com/Rheinwerk/ansible-role-install_root_ca_certs/actions/workflows/ci.yml/badge.svg)](https://github.com/Rheinwerk/ansible-role-install_root_ca_certs/actions/workflows/ci.yml)

Requirements
------------

The `ca-certificates` package (`update-ca-certificates`) and the CA certificates in PEM format.

Role Variables
--------------

Every variable has a default (`defaults/main.yml`); set only the ones that differ.
`meta/argument_specs.yml` and `tasks/assert.yml` check the values before anything
is written; a wrong type, a malformed certificate or the `_install_root_ca_certs` dict of v0.x
fails the run at the start.

| Variable | Default | Description |
| --- | --- | --- |
| `_install_root_ca_certs_certificates` | `{}` | CA certificates as `{<name>: <PEM certificate>}`, one certificate per entry. Each goes to `/usr/local/share/ca-certificates/<name>.crt`; the name may hold letters, digits, `_`, `.` and `-` and starts with a letter, digit or `_`. Each value must be exactly one PEM certificate with Unix line endings. |
| `_install_root_ca_certs_glob_file` | `/etc/cert_exp_time_globs` | Absolute path of a file that gets one line per installed certificate path, for certificate expiry checks; `""` skips it. |

The role installs nothing with the defaults; the certificates come from the play.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      vars:
        _install_root_ca_certs_certificates:
          example_root_ca: |
            -----BEGIN CERTIFICATE-----
            ...
            -----END CERTIFICATE-----
      roles:
        - { role: install_root_ca_certs, tags: ['install_root_ca_certs'] }

License
-------

Please see LICENSE.

Author Information
------------------

Original author is [Daniel Schneller](https://github.com/dschneller) as member of the [Rheinwerk](https://github.com/Rheinwerk) project.
