# Ansible-IOS-Backup-and-Restore

## Table of contents
* [General info](#general-info)
* [Technologies](#technologies)
* [Setup](#setup)

## General info
A simple Ansible playbook that can be used to automate the backup and restore of network device configurations.
	
## Technologies
Project is created with:
Ansible
	
## Setup
In this playbook, we assume that the hosts in the network_devices group are Cisco IOS devices. However, you can modify the playbook to work with other types of network devices as well.
The playbook performs the following steps:

1. Runs the ios_command module to get the running configuration of the device and saves it to the config variable.
2. Creates a backup directory on the Ansible control node using the file module.
3. Copies the configuration from the config variable to the backup directory using the copy module.
4. If the restore variable is defined, creates a restore directory on the Ansible control node using the file module.
5. If the restore variable is defined, copies the configuration from the backup directory to the restore directory using the copy module.
6. If the restore variable is defined, restores the configuration on the device using the ios_config module.

To use this playbook, you would need to define the network_devices group in your Ansible inventory file and set the ansible_network_os variable to ios. You would also need to define the restore variable if you want to restore a configuration.

For example, to backup the configurations of all devices in the network_devices group, you can run:
```
ansible-playbook backup_restore.yml
```
And to restore a configuration on a specific device, you can run:
```
ansible-playbook backup_restore.yml --extra-vars "restore=true" --limit hostname
```
Where hostname is the name of the device you want to restore the configuration to.

