# Ansible Role: `setup_server`

This Ansible role, `setup_server`, automates the setup and configuration of essential server settings and security protocols. It includes tasks for package installation, disk encryption, CPU optimizations, network interface management, and more, making it ideal for preparing servers for production or secure environments.

## Role Structure

- **`tasks/main.yml`**: The main playbook file that sequentially includes tasks for server setup.
- **Tasks**:
  - `install_packages.yml`: Installs essential packages in bulk.
  - `encrypt_second_disk.yml`: Encrypts the second disk in the system if it is available and unformatted.
  - `encrypt_empty_partition.yml`: Encrypts an empty partition on the disk containing the root partition.
  - `disable_c_states.yml`: Disables C-state for all available CPUs to optimize performance.
  - `switch_cpu_mode.yml`: Sets CPU operation mode to performance mode.
  - `rename_interface.yml`: Renames a network interface to `net0` for standardized naming.
  - `reboot_server.yml`: Reboots the server if required to apply changes.
  - `show_cpu_info.yml`: Displays CPU information, including details on cores and threads.

- **Helper Tasks** (invoked as needed by main tasks):
  - `encrypt_block_device.yml`: Encrypts and mounts a block device using LUKS.
  - `show_interface.yml`: Displays network interface details.

## Usage

Include the `setup_server` role in your Ansible playbook as follows:

```yaml
- hosts: all
  roles:
    - setup_server
