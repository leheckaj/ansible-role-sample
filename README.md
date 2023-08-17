Ansible Role: Wordpress
=========

Uninstalls nginx, installs Apache + MariaDB. In next step is downloaded and preconfigured Wordpress. Available only for Debian/Ubuntu Linux system.

Create file requirements.yml:
  
    - name: wordpress
    src: https://github.com/leheckaj/ansible-role-sample.git
    scm: git

From WSL:

      mkdir roles/
      ansible-galaxy install --role-file requirements.yml --roles-path roles/


This will install the role.

Requirements
------------

None.

Role Variables
--------------

A description of the settable variables for this role should go here:

  apache_domain: bsa-152.kiv.zcu.cz
  apache_docroot: /var/www/wordpress/
  

Dependencies
------------

None

Example Playbook
----------------

    ---
    - name: Install wordpress
      become: true
      become_user: root
      remote_user: admin
      hosts: 
          - localhost
      vars:
       apache_domain: bsa-152.kiv.zcu.cz
       apache_docroot: /var/www/wordpress/
      roles:
        - role: wordpress
      
      
License
-------

MIT/BSD

Author Information
------------------

This role was part of UWB KIV/BSA.
