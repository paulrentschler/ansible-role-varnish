paulrentschler.varnish
======================

[![MIT licensed][mit-badge]][mit-link]

Installs and configures the Varnish caching HTTP reverse proxy on Ubuntu Linux.


Requirements
------------

None.


Role Variables
--------------

The following variables are available with defaults defined in `defaults/main.yml`:



Dependencies
------------

None.


Example Playbook
----------------

Simple example:

    - hosts: all
      roles:
        - role: paulrentschler.varnish


License
-------

[MIT][mit-link]


Author Information
------------------

Created by Paul Rentschler in 2021.


[mit-badge]: https://img.shields.io/badge/license-MIT-blue.svg
[mit-link]: https://github.com/paulrentschler/ansible-role-varnish/blob/master/LICENSE
