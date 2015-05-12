Role Name
=========

This "perlbrew" role allow you to install perlbrew on Ubuntu / Debian / CentOS | RedHat.

[Perlbrew](http://perlbrew.pl) is a admin-free perl installation management
tool.

Requirements
------------

Ansible 1.6.x

Tested on
---------

1.8.2

Role Variables
--------------

* "perl_version" is used to specify the default perl version. Note: This
  cannot be `latest`, but need to be something like `perl-5.20.2`. The default
  will be changed to the latest stable.
* "perlbrew_user" is used to specify which user on the remote system that will
  get perlbrew.
* "http_proxy", "https_proxy" are used to access the internet through a proxy, default is undefined (disabled)
* "switch_to_new_perl" is used to activate (`perlbrew switch`) the new perl_version right away, default is `true` (if `false` added lines in `.profile`/`.bashrc` will be commented)
* "use_profile" add export PERLBREW_ROOT and source perlbrew rc files to `.profile`, default is `true` (if false adds to `.bashrc`)

Example config:

    ---
    perl_version: perl-5.20.2
    perlbrew_user: www
    http_proxy: http://myproxy:5865
    https_proxy: http://myproxy:5865
    switch_to_new_perl: true
    use_profile: true

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: jhthorsen.perlbrew, perlbrew_user: www, perl_version: perl-5.20.2 }

Another Example playbook
------------------------

Installs a system-wide perl in /opt/perlbrew using a proxy, do not activate it and add commented lines to user `.profile`):

    ---

    - name: Setup perlbrew
      hosts: all
      gather_facts: true

      roles:
        - {
            role: jhthorsen.perlbrew,
            perlbrew_user: root,
            perl_version: perl-5.21.11,
            perlbrew_root: /opt/perlbrew,
            http_proxy: "http://myproxy:5865",
            https_proxy: "http://myproxy:5865",
            switch_to_new_perl: false,
            use_profile: true
          }


License
-------

BSD

Author Information
------------------

Jan Henning Thorsen - jhthorsen@cpan.org - http://thorsen.pm
