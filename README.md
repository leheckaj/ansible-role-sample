Ansible Role: Wordpress
=========

Uninstalls nginx, installs Apache + MariaDB. In next step is downloaded and preconfigured Wordpress. Available only for Debian/Ubuntu Linux system.

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

Setup hosts file /etc/ansible/hosts:

    [servers]
    192.168.20.244

    [servers:vars]
    ansible_user=admin
    ansible_password=admin

Create your project folder

Create file requirements.yml in you project folder :
  
    - name: wordpress
    src: https://github.com/leheckaj/ansible-role-sample.git
    scm: git

From WSL in your project folder:

      mkdir roles/
      ansible-galaxy install --role-file requirements.yml --roles-path roles/


This will install the role.

Run the role:

      ansible-playbook main.yml
    


Create file main.yml:

    ---
    - name: Install wordpress
      become: true
      become_user: root
      remote_user: admin
      hosts: 
          - servers
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
