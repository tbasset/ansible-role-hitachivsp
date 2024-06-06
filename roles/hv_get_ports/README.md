Role Name
=========

Gets Port Data and returns port_data

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

    - name: Create Volume
      hosts: localhost
      vars_files:
        - storage.json
      vars:
        - myauthstring: "{{storage_username}}:{{storage_password}}"
    
        - volume_label: "{{my_volume_label}}"
        - volume_capacity_in_gb: "{{my_volume_size_in_gb}}"
        - host_group_name: "{{my_host_group}}"
      tasks:
        - name: Login
          import_role:
            name: hv_login
          when: (token_response.json.token is undefined)
    
        - name: Get Pool
          import_role:
            name: hv_get_ports
        - debug: var=port_data

        - name: Logout of Storage Array
          import_role:
            name: hv_logout





License
-------

BSD


