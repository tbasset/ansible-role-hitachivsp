Role Name
=========

GET WWN in Host Group using host_group_port variable and returns job_status

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

    - name: Login, Create Pool and Logout of Storage Array
      hosts: localhost
      vars_files:
        - storage.json
      vars:
        - myauthstring: "{{storage_username}}:{{storage_password}}"
          
        - host_group_port: "CL1-A"
    
      tasks:
        - name: Login to Storage Array
          import_role:
            name: hv_login
    
        - name: Get Host Groups
          import_role:
            name: hv_get_wwn
        - debug: var=host_wwns
    
        
        - name: Logout of Storage Array
          import_role:
            name: hv_logout



License
-------

BSD


