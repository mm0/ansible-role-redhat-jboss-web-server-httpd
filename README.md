Ansible role: "Red Hat JBoss Web Server - HTTPD" [![Build Status](https://travis-ci.org/Maarc/ansible-role-redhat-jboss-web-server-httpd.svg?branch=master)](https://travis-ci.org/Maarc/ansible-role-redhat-jboss-web-server-httpd)
=================================


Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.


Please have a look at [this example](https://github.com/Maarc/ansible_middleware_soe) showing how to easily operate Red Hat JBoss middleware products using this role.



Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.



Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.


Example Playbook
----------------

- hosts: "dev-jws-group"
  roles:
    # Red Hat JWS Apache instance
    - {role: "rh-jboss-web-server-httpd"}




License
-------

[Apache 2.0](./LICENSE)


Authors Information
------------------

* [Marc Zottner](https://github.com/Maarc)
* [Roeland van de Pol](https://github.com/roelandpol)
