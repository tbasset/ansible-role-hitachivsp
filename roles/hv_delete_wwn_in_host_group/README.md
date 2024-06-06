Role Name
=========

DELETE WWN from Host Group using wwn variable and returns job_status

Requirements
------------

An Hitachi Array with an PFrest interface.

Role Variables
--------------
* storage_username
* storage password
* wwn


Dependencies
------------

storage.json file

Example Playbook
----------------

    - name: Add WWN to Host Group
      hosts: localhost
      vars_files:
        - storage.json
      vars:
        - myauthstring: "{{storage_username}}:{{storage_password}}"
        
        - wwn: 
            hostWwn: "210003e08b0256f9"  
            portId: "CL1-A"  
            hostGroupNumber: 5
      tasks:
        - name: Login to Storage Array
          import_role:
            name: hv_login
        - name: Add WWN to Host Group
          import_role:
            name: hv_delete_wwn_in_host_group
        - name: Logout of Storage Array
          import_role:
            name: hv_logout


License
-------

BSD


