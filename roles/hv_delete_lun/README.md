Role Name
=========

Delete lunId from Host Group

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

    - name: Login, Create Pool and Logout of Storage Array
      hosts: localhost
      vars_files:
        - storage.json
      vars:
        - myauthstring: "{{storage_username}}:{{storage_password}}"
        - lun:
            portId: "CL2-A"
            hostGroupNumber: 1
    
      tasks:
        - name: Login to Storage Array
          import_role:
            name: hv_login
          when: token_response.json.token is undefined
    
        - name: Get Host Groups
          import_role:
            name: hv_get_host_group
        - debug: var=host_groups
    
    
        - name: Get LUNS
          import_role:
            name: hv_get_lun
        - debug: var=luns
    
        - name: Delete LUNS
          import_role:
            name: hv_delete_lun
        - debug: var=new_job_task
    
        - name: Logout of Storage Array
          import_role:
            name: hv_logout

    




License
-------

BSD


