Role Name
=========

Collectes a list of installed drives and returns drive_data variable. 

Requirements
------------

An Hitachi Array with an PFrest interface.

Role Variables
--------------
* storage_username
* storage password


Dependencies
------------

storage.json file

Example Playbook
----------------

    - name: Login and Logout of Storage Array
      hosts: localhost
      vars_files:
        - storage.json
      vars:
        - myauthstring: "{{storage_username}}:{{storage_password}}"
      tasks:
        - name: Login to Storage Array
          import_role:
            name: hv_login

        - name: Get Storage License information
          import_role:
            name: hv_get_drives
        - debug: var=drive_data

        - name: Logout of Storage Array
          import_role:
            name: hv_logout


License
-------

BSD


