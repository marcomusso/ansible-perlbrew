Role Name
=========

This "perlbrew" role allow you to install perlbrew on Ubuntu / Debian.

[Perlbrew](http://perlbrew.pl) is a admin-free perl installation management
tool.

Requirements
------------

Ansible 1.6.x

Role Variables
--------------

* "perl_version" is used to specify the default perl version. Note: This
  cannot be "latest", but need to be something like "perl-5.20.1". The default
  will be changed to the latest stable.
* "perlbrew_user" is used to specify which user on the remote system that will 
  get
  "perlbrew".

Example:

    ---
    perl_version: perl-5.20.1
    perlbrew_user: www

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: jhthorsen.perlbrew, user: www, perl_version: perl-5.20.1 }

License
-------

BSD

Author Information
------------------

Jan Henning Thorsen - jhthorsen@cpan.org - http://thorsen.pm

