MariaDB Ansible Role
=========

Configures my.cnf for MariaDB. It does not currently install MariaDB.

I use this for managing my.cnf on servers where MariaDB was installed using
the [Centminmod](http://centminmod.com/) bash script.

If you're using Centminmod, the following roles play well together:
  - **[centminmod wrapper](https://github.com/jeffwidman/ansible-centminmod)** (handles basic install + tuning common configuration settings)
  - **[mariadb](https://github.com/jeffwidman/ansible-mariadb)** (configures common my.cnf settings)
  - **[centminmod-domain-verification](https://github.com/jeffwidman/ansible-centminmod-domain-verification)** (tests that individual domains are configured properly)
  - **[php-fpm-pool](https://github.com/jeffwidman/ansible-php-fpm-pool)** (for creating/managing individual php-fpm pools for each PHP app)

Role Variables
--------------

You'll want to tweak `innodb_buffer_pool_size` and possibly
`innodb_buffer_pool_instances`.

The role default settings assume your server is using SSDs. If you're still running
spinning disks, you'll want to lower the `io` variables.

Example Playbook
----------------

    - hosts: servers
      roles:
        - { role: mariadb,
              innodb_buffer_pool_size: 1500M,
              innodb_buffer_pool_instances: 1,
              tags: ['mariadb', 'mysql'] }

License
-------

MIT

Author Information
------------------

Jeff Widman jeff@jeffwidman.com
