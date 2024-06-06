Role Name
=========

Collects Storage array information and returns it. Returns storage_data variable.

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
        - name: Get Storage information
          import_role:
            name: hv_get_storage
        - name: Logout of Storage Array
          import_role:
            name: hv_logout


License
-------

BSD


