paulrentschler.varnish
======================

[![MIT licensed][mit-badge]][mit-link]

Installs and configures the Varnish caching HTTP reverse proxy to run in front of a Plone website on Ubuntu Linux.


Requirements
------------

Plone CMS installed and configured to host a website that will be proxied by Varnish.


Role Variables
--------------

The following variables are available with defaults defined in `defaults/main.yml`:

Specify the version of Varnish to install. Version "3.0" and "4.0" are currently supported although the full functionality of the version 4.0 configuration is untested.

    varnish_version: 4.0


Specify the number of Zope clients available for Varnish to query. The Zope clients must start listening on port 8080 and use sequential ports from there.

    varnish_zope_clients: 1


Enable health checks against zope clients by specifying a url (including the Plone site name) to a static page in the site that is quick to load. **Disabled** by default.

    varnish_health_check_url: /Plone/about


Provide a custom 503 Service Unavailable message by specifying the absolute path on the file system to a HTML page that can be rendered instead of Varnish's default 503 page which is less than informative for the user. This page should exist outside of the Plone CMS and reference as few external files as possible to ensure that it loads and displays correctly to the user. **Disabled** by default.

    varnish_custom_503_filename: /path/to/document/root/with/error.html


Dependencies
------------

None.


Example Playbook
----------------

Minimal example that installs Varnish to run in front of a Plone site that only has one Zope client.

```yaml
---
- hosts: all
  roles:
     - paulrentschler.varnish
```

More common example that includes specifying the version of Varnish and the number of Zope clients.

```yaml
---
- hosts: all
  roles:
    - role: paulrentschler.varnish
      vars:
        varnish_version: 3.0
        varnish_zope_clients: 3
```

Complete example that shows specifying all of the possible variables.

```yaml
---
- hosts: all
  roles:
    - role: paulrentschler.varnish
      vars:
        varnish_version: 3.0
        varnish_zope_clients: 3
        varnish_health_check_url: /Plone/about
        varnish_custom_503_filename: /var/www/html/_meta/503error.html
```


License
-------

[MIT][mit-link]


Author Information
------------------

Created by Paul Rentschler in 2021.


[mit-badge]: https://img.shields.io/badge/license-MIT-blue.svg
[mit-link]: https://github.com/paulrentschler/ansible-role-varnish/blob/master/LICENSE
