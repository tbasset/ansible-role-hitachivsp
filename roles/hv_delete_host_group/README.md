Role Name
=========

Delete Host Group and returns job_status

Requirements
------------

An Hitachi Array with an PFrest interface.

Role Variables
--------------
* storage_username
* storage password
* host_group_port
* host_group_id


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
        - host_group_port: "CL1-A"
        - host_group_id: "1"
      tasks:
        - name: Login to Storage Array
          import_role:
            name: hv_login
        - name: Create Host Group
          import_role:
            name: hv_delete_host_group
        - name: Logout of Storage Array
          import_role:
            name: hv_logout


License
-------

BSD


