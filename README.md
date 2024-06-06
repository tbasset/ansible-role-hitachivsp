# Hitachi VSP Ansible Playbooks

## Overview:
Provision to and from your favourite hitachi array using sample playbooks that make use of the built-in REST framework native to following arrays at the time:
* Hitachi Virtual Storage Platform 5000 Series
* Hitachi Virtual Storage Platform E Series
* Hitachi Virtual Storage Platform G130, G/F350, G/F370, G/F700, G/F900

Adding a bunch of example workflow templates to the template folder.

## Requirements:
Create a storage.json file. Sample storage.json file below:
{
  "storage_ip": "192.168.0.1",
  "storage_username": "ma---------ce",
  "storage_password": "ra------------ce"
}

Will probably be better to store it in a vault file. 

This file contains your Hitachi array's SVP address in the case of Enterprise arrays or one of the controllers in the case of modular arrays. The username/password fields are for a user account native to the array. 

## Release Notes:
Added more templates and roles like: 
* get_wwn 
* get_stroage 
* get_status_resource
* get_parity_group
* get_license
* get_job_status
* get_host_group_details
* get_host_group
* get_drives
* get_ports
* delete_wwn_in_host_group
* delete_pool
* delete_lun
* delete_host_group
* create_pool
* create_host_group
* add_wwn_in_host_group 

## Example Playbooks:
- ansible-playbook templates/workflow_login_logout.yaml
- ansible-playbook templates/workflow_create_host_group.yaml
- ansible-playbook templates/workflow_create_one_host_group.yaml
- ansible-playbook templates/workflow_create_pool.yaml
- ansible-playbook templates/workflow_create_pool_and_delete_pool.yaml
- ansible-playbook templates/workflow_create_volume_from_first_pool_and_assign_to_hostgroup.yaml
- \# ansible-playbook templates/workflow_delete_host_group.yaml
- \# ansible-playbook templates/workflow_delete_luns_from_host_group.yaml
- \# ansible-playbook templates/workflow_delete_pool.yaml
- ansible-playbook templates/workflow_get_host_group.yaml
- ansible-playbook templates/workflow_get_host_group_details.yaml
- ansible-playbook templates/workflow_get_wwns.yaml
- ansible-playbook templates/workflow_login.yaml
- ansible-playbook templates/workflow_login_logout.yaml
- ansible-playbook templates/workflow_logout.yaml

### Version: 00.1:
Initial release, publishing items to Ansible galaxy with an example of creating volume using built in PFRest interface. Added:
* login
* logout
* add_lun
* change_ldev_name
* create_volume
* get_host_group
* get_job_status
* get_pool_data

## Example Playbooks:
- ansible-playbook templates/workflow_login_logout.yaml
