PHP
===

Install and configure PHP

Requirements
------------

If using PHP-FPM, the configured system user and group must already exist on the system. PHP-FPM will be installed and configured when `fpm` is in the `php_packages` list.


Role Variables
--------------

	# Required if using FPM
	php_fpm_user: (system user)
	php_fpm_group: (system group)

	# Optional, defaults shown
	php_version: php56
	php_fpm_listen: /var/run/php-fpm.sock
	php_packages:
	  - fpm
	  - pdo
	  - opcache
	  - cli
	  - mcrypt
	  - common

`php_version` can be any of `php54`, `php55`, `php56`, or `php70`. Use of PHP5.4 is strongly discouraged as it is [no longer maintained](http://php.net/supported-versions.php). 5.5 will receive secutity fixes only until 2016-07-10.

Specifying an exact point release is not supported at this time.
	  
Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: Firehed.php
           php_version: php70
           php_packages:
             - fpm
             - common
             - cli
             - pecl-memcached

License
-------

MIT