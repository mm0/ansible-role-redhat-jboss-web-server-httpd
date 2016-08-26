Ansible role: "Red Hat JBoss Web Server - HTTPD" [![Build Status](https://travis-ci.org/Maarc/ansible-role-redhat-jboss-web-server-httpd.svg?branch=master)](https://travis-ci.org/Maarc/ansible-role-redhat-jboss-web-server-httpd)
=================================

Description
-----------

Please have a look at [this example](https://github.com/Maarc/ansible_middleware_soe) showing how to easily operate Red Hat JBoss middleware products using this role.


Requirements
------------

This role has been tested on Ansible 2.0.2.0 and 2.1.1.0. It requires Red Hat Enterprise Linux 7.


Role Variables
--------------

    A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.


Dependencies
------------

The "Maarc.rh-jboss-common" role is required. It could be imported as follows:

    ansible-galaxy install Maarc.rh-jboss-common -p roles

or

    ansible-galaxy install -r requirements.yml -p roles


Installation
------------

    ansible-galaxy install Maarc.rh-jboss-web-server-httpd -p roles



Example Playbook
----------------

    - hosts: "dev-jws-group"
      roles:
        - {role: "Maarc.rh-jboss-web-server-httpd"}


License
-------

[Apache 2.0](./LICENSE)


Authors Information
------------------

* [Marc Zottner](https://github.com/Maarc)
* [Roeland van de Pol](https://github.com/roelandpol)
