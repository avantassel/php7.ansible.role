# Ansible Role: PHP7

[![Build Status](https://travis-ci.org/avantassel/php7.ansible.role.svg?branch=master)](https://travis-ci.org/avantassel/php7.ansible.role)

An Ansible role of Deploy PHP 7 (php-fpm) for nginx on CentOS, Debian, and Ubuntu. (forked from [https://galaxy.ansible.com/chusiang/php7/](https://galaxy.ansible.com/chusiang/php7/))

* Current PHP7 version: **7.0.4**

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    # Ubuntu
    php_ppa: "ppa:ondrej/php"    
    php_packages:
      - php7.0-common
      - php7.0-cli
      - php7.0-intl
      - php7.0-curl
      - php7.0-cgi
      - php7.0-fpm
      - php7.0-pear
      - php7.0-json
      - php7.0-gd

    php_timezone: Asia/Taipei
    php_upload_max_filesize: "20M"
    php_post_max_size: "20M"
    php_memory_limit: "1024M"
    php_owner: nginx
    php_group: nginx

### Note

1. If you see some error message, maybe you need modify `php_owner` and `php_group` from **nginx** to **www-data**.

 * Browser:

     > `An error occurred.`

 * error.log:

     > `connect() to unix:/var/run/php/php7.0-fpm.sock failed (13: Permission denied) while connecting to upstream ...`

2. The `/target/path/` of **socket**, configure files is difference on Ubuntu and CentOS. **Be careful your Nginx setting !**

 * Ubuntu:
      * Configure:
         * `/etc/php/7.0/fpm/php.ini`
         * `/etc/php/7.0/cli/php.ini`
     * Socket: `/var/run/php/php7.0-fpm.sock`

 * CentOS:
     * Configure:
         * `/etc/php-fpm.d/www.conf`
         * `/etc/php.ini`
     * Socket: `/run/php-fpm/www.sock`

## Dependencies

None.

## Example Playbook

    - hosts: webservers
      roles:
        - { role: chusiang.php7 }

## License

MIT
