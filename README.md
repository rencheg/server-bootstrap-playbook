# Ansible Playbook: `prepare_new_server.yml`


## Overview

The `prepare_new_server` Ansible playbook automates the initial setup and configuration of a server. It includes tasks for system customization, package installation, disk encryption, and network configuration, making it a comprehensive solution for provisioning servers in development or production environments.


## Structure

- **`ansible.cfg`**: Config file specifying Ansible options.
- **`inventories/`**: Contains host and group variables.
  - `group_vars/all.yml`: Global settings for all hosts
  - `group_vars/bootstrap.yml`: Global settings for new servers, bootstrap group.
  - `host_vars/bhft_test_vm.yml`: Specific settings for test host.
  - `hosts.yml`: Defines the inventory of managed servers.
- **`playbooks/prepare_new_server.yml`**: The main playbook file to initiate server setup.
- **`roles/setup_server/`**: Role with specific configuration tasks:
  - `tasks/`: Task files for detailed configurations, including package installation, disk encryption, CPU settings, and network interface customization.


## Variables for Bootstrap Group

The following variables in `group_vars/bootstrap.yml` define configuration options for servers in the bootstrap group:

- **`ansible_user`**: Specifies the user for SSH access.
  - Default: `ubuntu`
- **`encrypted_empty_partition_label`**: Label for encrypted empty partition on disk with root partition.
  - Default: `data`
- **`encrypted_empty_disk_label`**: Label for encrypted empty disk.
  - Default: `storage`

## Sensitive variables encryption

Ansible Vault is used for encryption of sensitive variables
Encrypted variables are stored in host_vars files on per-host basis.
Vault masterpassword is stored in **'vault_pass.txt'** file

## Usage

Run the playbook with the following command:

```bash
ansible-playbook playbooks/prepare_new_server.yml --vault-password-file vault_pass.txt
