## Dynamic Inventory
```
Static inventory files worked for small infrastructure.
In a virtual or cloud computing environment. 
API for cloud providers, Cobbler, LDAP directories, or other third-party configuration management database (CMDB)

Dynamically generated inventories: 
    - inventory plug-ins
    - inventory scripts 
```

## Command for inventory plug-ins 
```sh 
[user@host ~]# ansible-navigator doc --mode stdout --type inventory --list 
[user@host ~]# ansible-navigator doc --mode stdout --type inventory redhat.satellite.foreman
[user@host ~]# ansible-navigator inventory --mode stdout -i inventory --list
```

## Ansible Multiple Invnetories 
```
Ansible supports the use of mulitple inventory in the same run. 
All inventory file included in the directory, either static or dynamic, are combined to determine the inventory. 
```

## Static inventory change from yaml to json 
```sh
[user@host ~]# ansible-navigator inventory --mode stdout -i origin_inventory --list --yaml
[user@host ~]# ansible-navigator inventory -i static-inventory.yml --list --mode stdout --eei registry.redhat.io/ansible-automation-platform-24/ee-supported-rhel8:latest --pp misisng
```

## Host and Group Variable Precedence 
```
The precedence order for these variables is as follows, from lowest to highest:
Group variables (in ascending order of precedence):
- Set directly in an inventory file or by a dynamic inventory script
- For all set in the inventory group_vars/all file or subdirectory
- For all set in the playbook group_vars/all file or subdirectory
- For other groups set in the inventory group_vars/ subdirectory
- For other groups set in the playbook group_vars/ subdirectory
Host variables (in ascending order of precedence):
- Set directly in an inventory file or by a dynamic inventory script
- Set in the inventory host_vars/ subdirectory
- Set in the playbook host_vars/ subdirectory
Host facts and cached facts
```