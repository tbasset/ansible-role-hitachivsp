Role Name
=========

Collects Storage array license information and returns it. Returns license_data variable.

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
            name: hv_get_license
        - name: Logout of Storage Array
          import_role:
            name: hv_logout


License
-------

BSD


