Role Name
=========

Create pool on Array

Requirements
------------

An Hitachi Array with an PFrest interface.

Role Variables
--------------
* storage_username
* storage password
* pool_name        # Pool Name
* is_encrypted     # Pool Encryption Enabled, default false
* raid_level       # Raid level to use. 
* data_drive_count # Number of Drives to ADD.
* drive_type_code  # where useOfTheDrive='free' from hv_get_drives role.


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
        - is_encrypted: false
        - pool_name: "Production"
        - raid_level: "RAID6" # Raid level to use. 
        - data_drive_count: 8 # Number of Drives to ADD.
        - drive_type_code: SNB5B-R1R9NC # where useOfTheDrive='free' from hv_get_drives role.
      tasks:
        - name: Login to Storage Array
          import_role:
            name: hv_login
        - name: Get Storage License information
          import_role:
            name: hv_create_pool
        - name: Logout of Storage Array
          import_role:
            name: hv_logout


License
-------

BSD


