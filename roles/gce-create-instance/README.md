
# GCE ROLE

WARNING: This role is compatible only with Ansible v2.4

Role used to create instances in GCE from playbook

## Available variables:

gce_instance_name
gce_machine_type
gce_image
gce_state
gce_project_id
gce_disk_size
gce_disk_auto_delete
gce_tags
gce_external_ip

The zone of the machine is determined by parsing the hostname using core role

zone: "{{ REGION.stdout }}-central1-{{ ZONE.stdout }}"


## 
### Additional disks vars

add_disk: False  # additional disks creation switched off by default

disks_dict: ""

## EXAMPLE ( adding 2 disks )

ansible-playbook ... ... -e "{'disks_dict': {'disk1': {'disk_name': 'asp-disk', 'disk_size': '11'}, 'disk2': {'disk_name': 'asp-disk2', 'disk_size': '12'}}}"
