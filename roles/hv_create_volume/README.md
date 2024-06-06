Role Name
=========

Create Volume

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
            name: hv_get_pool_data
        - name: "Set My Pool to use"
          set_fact:
            pool_id: "{{ pool_data.json.data.0.poolId }}"
          when: (pool_data.json.data|length >0) and (pool_id is undefined)
        - debug: var=pool_data.json.data.0
    
        - name: Create Volume
          import_role:
            name: hv_create_volume
    
        - name: Get Job Status
          import_role:
            name: hv_get_job_status
        - debug: var=job_status_response.json.affectedResources
        - debug: var=job_status_response
          when: (job_status_response.json.affectedResources is undefined)
    
        - name: Set Created LDEVID Name
          set_fact:
            my_ldevId: '{{job_status_response.json.affectedResources.0.split("/")[-1]}}'
    
        - name: Display created LdevID
          ansible.builtin.debug:
            msg: "My LdevID: {{ my_ldevId }}"
    
        - name: Change LDEV Name
          import_role:
            name: hv_change_ldev_name
    
        - name: Get Job Status
          import_role:
            name: hv_get_job_status
        - debug: var=job_status_response
          when: (job_status_response.json.affectedResources is undefined)
    
        - name: Get Host Groups
          import_role:
            name: hv_get_host_group
    
        - name: Add Lun
          import_role:
            name: hv_add_lun





License
-------

BSD


