Ansible Role: Guacamole
=========

This Ansible role will configure Apache's Guacamole on Ubuntu 16.04 (Xenial)
complete with MariaDB.

It is *strongly* advised that you run `mysql_secure_installation` after this is run. This role does *not* create a MariaDB root password.

Requirements
------------

Works with Ansible 2.4.

Requires `become` or running as the `root` user. You can use `--ask-become-pass` when running.

Role Variables
--------------
The following variables are set in `defaults/main`:

| Variable                 | Description                  | Default                      |
|--------------------------|------------------------------|-------------------------------
|guacamole_version         | Guacamole version to install | currently `0.9.13-incubating`|
|guacamole_db_user         | Guacamole MariaDB username   | `guacamole`                  |
|guacamole_db_password     | Guacamole MariaDB password   | `foo`                        |
|guacamole_db_name         | Guacamole MariaDB database   | `guacamole_db`               |
|mysql_java_client_version | MySQL Java Client version    | `5.1.44`                     |
|guacamole_apt_install     | Apt packages to install      | Lots!                        |

*Note:* For earlier versions of Ubuntu than 16.04, some packages will be different,
specifically `libjpeg` and `tomcat`. You can override the versions in your own variables file.

Example Playbook
----------------

```
- hosts: guacamole-host
  become: yes
  roles: 
    - alexfeig.guacamole
```

 Information
------------------

This role was created by [Alex Feigenson](https://github.com/alexfeig)

To Do List
------------------

* Maybe add in an nginx proxy
* Make MariaDB an optional install
* Add travis integration (need to account for 16.04)
