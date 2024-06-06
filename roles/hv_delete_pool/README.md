Role Name
=========

Delete Pool ID on storage array. 

Requirements
------------

An Hitachi Array with an PFrest interface.

Role Variables
--------------
* storage_username
* storage password
* pool_id        # Pool Id



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
        - pool_id: 0 # Pool ID to delete
      tasks:
        - name: Login to Storage Array
          import_role:
            name: hv_login
        - name: Get Storage License information
          import_role:
            name: hv_delete_pool
        - name: Logout of Storage Array
          import_role:
            name: hv_logout


License
-------

BSD


