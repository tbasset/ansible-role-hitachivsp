Role Name
=========

Get host Group data returns 'host_groups' variable

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
    
        - pool_id: 0
    
      tasks:
        - name: Login to Storage Array
          import_role:
            name: hv_login
          when: (token_response.json.token is undefined)
    
        - name: Get Host Groups
          import_role:
            name: hv_get_host_group
        - debug: var=host_groups

    






License
-------

BSD


