# Ansible-IOS-Backup-and-Restore
A simple Ansible playbook that can be used to automate the backup and restore of network device configurations.
In this playbook, we assume that the hosts in the network_devices group are Cisco IOS devices. However, you can modify the playbook to work with other types of network devices as well.

The playbook performs the following steps:

  Runs the ios_command module to get the running configuration of the device and saves it to the config variable.
  Creates a backup directory on the Ansible control node using the file module.
  Copies the configuration from the config variable to the backup directory using the copy module.
  If the restore variable is defined, creates a restore directory on the Ansible control node using the file module.
  If the restore variable is defined, copies the configuration from the backup directory to the restore directory using the copy module.
  If the restore variable is defined, restores the configuration on the device using the ios_config module.
To use this playbook, you would need to define the network_devices group in your Ansible inventory file and set the ansible_network_os variable to ios. You would also need to define the restore variable if you want to restore a configuration.
