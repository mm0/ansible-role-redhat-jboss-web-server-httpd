mm0.rh-jboss-web-server-httpd
=======

[![Build Status](https://travis-ci.org/mm0/ansible-role-redhat-jboss-web-server-httpd.svg?branch=master)](https://travis-ci.org/mm0/ansible-role-redhat-jboss-web-server-httpd) [![Galaxy](https://img.shields.io/badge/galaxy-mm0.rh--jboss--web--server--httpd-blue.svg?style=flat)](https://galaxy.ansible.com/mm0/rh-jboss-web-server-httpd)

Description
-----------

Please have a look at [this example](https://github.com/Maarc/ansible_middleware_soe) showing how to easily operate Red Hat JBoss middleware products using this role.

The final installation will be found in the `httpd` subdirectory of the `jboss_jws_home` directory

Requirements
------------

This role has been tested on Ansible 2.0.2.0 and 2.1.1.0. It requires Red Hat Enterprise Linux 7.

The following files must be present on server:

| Ansible Variable(s)  | Default Value       | Description          |
|-------------------|---------------------|----------------------|
| `jboss_jws_golden_image_dir` | `/mnt/nfs/ansible/redhat/rh_jboss_binaries/` | Directory of zip |
| `jws_httpd_zip_artifact_name` | `jws-httpd-3.0.3-RHEL7-x86_64` | Base name of zip file (without .zip extension) |

Customize installation with the following variables:

| Name              | Default Value       | Description          |
|-------------------|---------------------|----------------------|
| `jboss_jws_instance_name` | `Default` | Environment name for deployment|
| `jboss_jws_instance_port_offset`, `jboss_jws_instance_ssl_port_offset`, `jboss_jws_mod_cluster_port_offset` | `0` | Port offset |
| `jboss_jws_bind_ip_address` | `0.0.0.0` | Interface to bind to |
| `jws_server_admin` | `test@test.com` | Email of Admin for Apache|
| `jws_server_name` | `website.com` | Hostname |
| `jws_required_ips` | `["127.0.0.1", "10.0.0.0/8" ]` | [List] IP Ranges to whitelist for mod_cluster mod_cluster-manager |




Role Variables
--------------


*General variables*

| Name              | Default Value       | Description          |
|-------------------|---------------------|----------------------|
| `jboss_jws_golden_image_dir` | `/mnt/nfs/ansible/redhat/rh_jboss_binaries` | Directory location of golden image zip |
| `jboss_jws_instance_name` | `default` |  Name of the separate running Red Hat JBoss JWS instance |
| `java_pkg_name` | `java-1.8.0-openjdk-devel` | Used java version: Java 8 JDK.  |
| `jboss_java_home` | `/usr/lib/jvm/java-1.8.0-openjdk` | Default JAVA_HOME |
| `user_limits` | `See Defaults/main.yml` | Default User Limits |
| `jws_server_admin` | `admin@admin.com` | Default Apache Admin email |
| `jws_server_name` | `site.site.com` | Default ServerName |
| `jws_httpd_zip_artifact_name` | `jws-httpd-3.0.3-RHEL7-x86_64` | Installation Zip basename|
| `jboss_jws_instance_service_name` | `"jws_apache_{{ jboss_jws_instance_name }}"` | Installation Environment/Name|
| `jws_apache` | `See Defaults/main.yml` | Dictionary with user account of app |
| `jws_required_ips` | `See Defaults/main.yml` | List of Allowed IPs/Ranges for Mod Cluster Manager|
| `jws_httpd_zip_artifact_dl_dst` | `"{{ jboss_jws_golden_image_dir }}/{{ jws_httpd_zip_artifact_name }}.zip"` | Install Archive Location |
| `jboss_jws_home` | `"{{ jws_apache.user_home }}/{{ jboss_jws_instance_name }}/jws-{{jboss_jws_version}}"` | Directory containing the unpacked golden image. |
| `jboss_jws_instance_dir` | `"{{ jws_apache.user_home }}/{{ jboss_jws_instance_name }}"` | Directory for the target running instance |




*Ports Variables*

| Name              | Default Value       | Description          |
|-------------------|---------------------|----------------------|
| `jboss_jws_instance_default_port` | `9000` |  Default Port |
| `jboss_jws_instance_ssl_default_port` | `9001` |  Default SSL Port |
| `jboss_jws_mod_cluster_default_port` | `6666` |  Default Mod Cluster Listener Port|
| `jboss_jws_instance_default_port` | `83` |  Default web listener port |
| `jboss_jws_instance_port_offset` | `0` |  Port offset |
| `jboss_jws_instance_ssl_port_offset` | `0` |  Port offset |
| `jboss_jws_mod_cluster_port_offset` | `0` |  Port offset|




Dependencies
------------

None

Installation
------------

    ansible-galaxy install mm0.rh-jboss-web-server-httpd -p roles

Is it recommended to add this role to your project's `requirements.yml` file and use ansible-galaxy

Example Playbook
----------------

```yaml
- hosts: "dev-jws-group"
  vars:
  - jboss_jws_instance_name: "dev4"
  - jboss_jws_instance_port_offset: "30"
  - jboss_jws_instance_ssl_port_offset: "30"
  - jboss_jws_mod_cluster_port_offset: "30",
  - jboss_jws_bind_ip_address: "{{ ansible_ens160.ipv4.address }}"
  - jws_server_admin: email@email.com
  - jws_server_name: az.yb.com
  roles:
    - {role: "mm0.rh-jboss-web-server-httpd"}
```

Tags
----
##### Stopping JWS Service
```bash
ansible-playbook deploy-jboss-httpd.yml -e 'target=rh72'  -t stop_jws
```
##### (Re)starting JWS Service
```bash
ansible-playbook deploy-jboss-httpd.yml -e 'target=rh72'  -t start_jws
```


License
-------

[Apache 2.0](./LICENSE)


Authors Information
------------------

* [Marc Zottner](https://github.com/Maarc)
* [Roeland van de Pol](https://github.com/roelandpol)
