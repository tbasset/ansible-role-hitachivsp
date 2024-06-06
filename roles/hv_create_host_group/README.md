Role Name
=========

Create a new Host Group

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

    - name: Login and Logout of Storage Array
      hosts: localhost
      vars_files:
        - storage.json
      vars:
        - myauthstring: "{{storage_username}}:{{storage_password}}"
        
        - host_group: 
            portId: CL1-A
            hostGroupName: MyVMWARECluster
            hostModeOptions:
              - 54
              - 63
              - 114
            hostMode: VMWARE_EX
      tasks:
        - name: Login to Storage Array
          import_role:
            name: hv_login
        - name: Create Host Group
          import_role:
            name: hv_create_host_group
        - name: Logout of Storage Array
          import_role:
            name: hv_logout


License
-------

BSD


