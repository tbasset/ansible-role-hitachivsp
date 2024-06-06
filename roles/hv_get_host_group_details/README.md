Role Name
=========

Get Host Group Details of a specific host group.

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

        - host_group_port: "CL1-A"
        - host_group_id: "1"
      tasks:
        - name: Login to Storage Array
          import_role:
            name: hv_login
          when: (token_response.json.token is undefined)



        - name: Get Host Group Detials
          import_role:
            name: hv_get_host_group_details
        - debug: var=host_groups








License
-------

BSD


