Role Name
=========

Add WWN to Host Group using wwn variable and returns job_status

Requirements
------------

An Hitachi Array with an PFrest interface.

Role Variables
--------------
* storage_username
* storage password
* host_group


Dependencies
------------

storage.json file

Example Playbook
----------------

    
    - name: Add WWN to Lun
      hosts: localhost
      vars_files:
        - storage.json
      vars:
        - myauthstring: "{{storage_username}}:{{storage_password}}"
        - wwn:
            hostWwn: "100000109b41bc22"
            portId: "CL2-A"
            hostGroupNumber: 1
    
    
      tasks:
        - name: Login to Storage Array
          import_role:
            name: hv_login
          when: (token_response.json.token is undefined)
    
        - name: "Add WWN {{wwn.hostWwn}} to Host Group {{wwn.portId}}-{{wwn.hostWwn}}"
          import_role:
            name: hv_add_wwn_in_host_group




License
-------

BSD


