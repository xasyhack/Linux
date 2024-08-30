# Linux
# CentOS 7 Administration Cheat Sheet

## System Information
| Command                        | Description                                               |
|--------------------------------|-----------------------------------------------------------|
| `uname -a`                     | Display system information (kernel version, hostname, etc.)|
| `hostnamectl`                  | View and change hostname                                  |
| `uptime`                       | Show how long the system has been running                 |
| `free -m`                      | Display memory usage in MB                                |
| `df -h`                        | Display disk space usage in human-readable format         |
| `lsblk`                        | List information about block devices                      |

## User Management
| Command                             | Description                                                |
|-------------------------------------|------------------------------------------------------------|
| `useradd <username>`                | Create a new user                                          |
| `passwd <username>`                 | Set or change a user's password                            |
| `usermod -aG <group> <username>`    | Add a user to a group                                      |
| `userdel <username>`                | Delete a user                                              |
| `groupadd <groupname>`              | Create a new group                                         |
| `groups <username>`                 | List groups for a user                                     |

## File Permissions
| Command                                 | Description                                                |
|-----------------------------------------|------------------------------------------------------------|
| `chmod <permissions> <file>`            | Change file or directory permissions                       |
| `chown <user>:<group> <file>`           | Change ownership of a file or directory                    |
| `chgrp <group> <file>`                  | Change group ownership of a file or directory              |
| `umask`                                 | Set default file permissions                               |

## Package Management
| Command                           | Description                                                |
|-----------------------------------|------------------------------------------------------------|
| `yum update`                      | Update all packages                                        |
| `yum install <package>`           | Install a package                                          |
| `yum remove <package>`            | Remove a package                                           |
| `yum list installed`              | List all installed packages                                |
| `yum search <package>`            | Search for a package                                       |

## Service Management
| Command                            | Description                                                |
|------------------------------------|------------------------------------------------------------|
| `systemctl start <service>`        | Start a service                                            |
| `systemctl stop <service>`         | Stop a service                                             |
| `systemctl restart <service>`      | Restart a service                                          |
| `systemctl enable <service>`       | Enable a service to start at boot                          |
| `systemctl disable <service>`      | Disable a service from starting at boot                    |
| `systemctl status <service>`       | Check the status of a service                              |

## Networking
| Command                                         | Description                                                |
|-------------------------------------------------|------------------------------------------------------------|
| `ip addr show`                                  | Display IP address and network interfaces                  |
| `nmcli device status`                           | Show the status of network devices                         |
| `nmcli con up <connection-name>`                | Bring up a network connection                              |
| `ping <host>`                                   | Test network connectivity                                  |
| `firewall-cmd --permanent --add-service=<service>` | Open a service in the firewall (e.g., HTTP, SSH)           |
| `firewall-cmd --reload`                         | Reload the firewall to apply changes                       |

## Filesystem
| Command                                 | Description                                                |
|-----------------------------------------|------------------------------------------------------------|
| `mount /dev/<device> /mnt`              | Mount a device to a directory                              |
| `umount /mnt`                           | Unmount a device                                           |
| `mkfs.ext4 /dev/<device>`               | Format a device with ext4 filesystem                       |
| `ls -l`                                 | List files in a directory with detailed information        |
| `du -sh <directory>`                    | Show the size of a directory                               |

## Process Management
| Command                       | Description                                                |
|-------------------------------|------------------------------------------------------------|
| `ps aux`                      | Display running processes                                  |
| `top`                         | Interactive process viewer                                 |
| `kill <PID>`                  | Terminate a process by PID                                 |
| `killall <process_name>`      | Terminate all processes with the given name                |

## Cron Jobs
| Command                           | Description                                                |
|-----------------------------------|------------------------------------------------------------|
| `crontab -e`                      | Edit the current user's crontab                            |
| `crontab -l`                      | List the current user's cron jobs                          |
| `systemctl restart crond`         | Restart the cron service                                   |

## SELinux
| Command                                                      | Description                                                |
|--------------------------------------------------------------|------------------------------------------------------------|
| `getenforce`                                                 | Check the current SELinux mode (Enforcing, Permissive, or Disabled) |
| `setenforce 0`                                               | Set SELinux to permissive mode temporarily                 |
| `semanage fcontext -a -t httpd_sys_content_t "/web(/.*)?"`   | Set SELinux context for web directories                    |
| `restorecon -Rv /web`                                        | Apply SELinux context to a directory recursively           |

## Logs and Monitoring
| Command                           | Description                                                |
|-----------------------------------|------------------------------------------------------------|
| `journalctl -xe`                  | View system logs and errors                                |
| `tail -f /var/log/messages`       | Monitor the system log in real-time                        |
| `dmesg`                           | Display kernel ring buffer messages (hardware logs)        |

## Security
| Command                           | Description                                                |
|-----------------------------------|------------------------------------------------------------|
| `passwd`                          | Change the current user's password                         |
| `visudo`                          | Edit the sudoers file                                      |
| `firewall-cmd --list-all`         | List all active firewall rules                             |
| `iptables -L`                     | List all iptables rules                                    |

## Remote Access
| Command                                              | Description                                                |
|------------------------------------------------------|------------------------------------------------------------|
| `ssh user@hostname`                                  | SSH into a remote server                                   |
| `scp file user@hostname:/path/to/destination`        | Securely copy a file to a remote server                    |
| `rsync -avz /src user@hostname:/dest`                | Synchronize files between local and remote systems         |

## Backup and Restore
| Command                                                      | Description                                                |
|--------------------------------------------------------------|------------------------------------------------------------|
| `tar -czvf backup.tar.gz /path/to/directory`                 | Create a compressed backup of a directory                  |
| `tar -xzvf backup.tar.gz`                                    | Extract a compressed backup                                |
| `rsync -av /source /destination`                             | Backup files using rsync                                   |

# CentOS Enterprise Linux 7 User and Group Management Cheat Sheet

## User Management

| **Command**                      | **Description**                                                |
|----------------------------------|----------------------------------------------------------------|
| `useradd <username>`             | Create a new user with the specified username.                 |
| `passwd <username>`              | Set or change the password for the specified user.             |
| `usermod -aG <group> <username>` | Add an existing user to a specified group.                     |
| `userdel <username>`             | Delete the specified user.                                     |
| `userdel -r <username>`          | Delete the specified user and their home directory.            |
| `id <username>`                  | Display the user ID (UID) and group ID (GID) information.      |
| `whoami`                         | Display the username of the current user.                      |
| `lastlog`                        | Display the last login information for all users.              |

## Group Management

| **Command**                      | **Description**                                                |
|----------------------------------|----------------------------------------------------------------|
| `groupadd <groupname>`           | Create a new group with the specified name.                    |
| `groupdel <groupname>`           | Delete the specified group.                                    |
| `gpasswd -a <username> <group>`  | Add a user to a group.                                         |
| `gpasswd -d <username> <group>`  | Remove a user from a group.                                    |
| `groups <username>`              | Display all groups the specified user belongs to.              |
| `newgrp <group>`                 | Log in to a new group session.                                 |
| `getent group <groupname>`       | Display group information from the system databases.           |

## File and Directory Permissions

| **Command**                               | **Description**                                                |
|-------------------------------------------|----------------------------------------------------------------|
| `chmod <permissions> <file>`              | Change the permissions of a file or directory.                 |
| `chown <user>:<group> <file>`             | Change the owner and group of a file or directory.             |
| `chgrp <group> <file>`                    | Change the group ownership of a file or directory.             |
| `umask`                                   | Display or set the default file creation permissions mask.     |
| `ls -l`                                   | List files and directories with their permissions.             |
| `find / -user <username>`                 | Find all files and directories owned by a specified user.      |
| `find / -group <groupname>`               | Find all files and directories belonging to a specified group. |

## Sudo Management

| **Command**                          | **Description**                                                |
|--------------------------------------|----------------------------------------------------------------|
| `visudo`                             | Edit the sudoers file to grant or revoke sudo privileges.      |
| `sudo <command>`                     | Execute a command with elevated privileges.                   |
| `sudo -l`                             | List the allowed and forbidden commands for the current user.  |

## User and Group Information Files

| **File**                      | **Description**                                                |
|-------------------------------|----------------------------------------------------------------|
| `/etc/passwd`                 | Contains user account information.                             |
| `/etc/shadow`                 | Contains encrypted passwords and account expiration data.      |
| `/etc/group`                  | Contains group information.                                    |
| `/etc/gshadow`                | Contains group passwords (if any) and group administrator information. |


# CentOS Enterprise Linux 7 Storage Management Cheat Sheet

## Disk and Partition Management

| **Command**                        | **Description**                                                    |
|------------------------------------|--------------------------------------------------------------------|
| `lsblk`                            | List all block devices, including partitions and LVM volumes.      |
| `fdisk -l`                         | List partitions on all disks.                                      |
| `fdisk /dev/sdX`                   | Create, modify, or delete partitions on `/dev/sdX`.                |
| `parted /dev/sdX`                  | Advanced partition management, supporting GPT and MBR.             |
| `mkfs.ext4 /dev/sdXn`              | Create an ext4 filesystem on the partition `/dev/sdXn`.            |
| `mkfs.xfs /dev/sdXn`               | Create an XFS filesystem on the partition `/dev/sdXn`.             |
| `blkid`                            | Display UUID and type information for block devices.               |
| `df -h`                            | Display disk usage in human-readable format.                       |
| `mount /dev/sdXn /mnt`             | Mount a partition to a directory.                                  |
| `umount /mnt`                      | Unmount a partition from a directory.                              |
| `swapoff -a`                       | Disable all swap partitions.                                       |
| `swapon /dev/sdXn`                 | Enable a swap partition on `/dev/sdXn`.                            |

## Logical Volume Management (LVM)

| **Command**                        | **Description**                                                    |
|------------------------------------|--------------------------------------------------------------------|
| `pvcreate /dev/sdXn`               | Initialize a physical volume on `/dev/sdXn`.                       |
| `vgcreate <vgname> /dev/sdXn`      | Create a volume group with the specified name.                     |
| `lvcreate -L 10G -n <lvname> <vgname>` | Create a logical volume with the specified size and name.          |
| `lvextend -L +5G /dev/<vgname>/<lvname>` | Extend a logical volume by 5 GB.                                   |
| `resize2fs /dev/<vgname>/<lvname>` | Resize the filesystem on a logical volume after extending it.      |
| `lvremove /dev/<vgname>/<lvname>`  | Remove a logical volume.                                           |
| `vgextend <vgname> /dev/sdXn`      | Add a physical volume to an existing volume group.                 |
| `vgreduce <vgname> /dev/sdXn`      | Remove a physical volume from a volume group.                      |
| `pvs`, `vgs`, `lvs`                | Display information about physical volumes, volume groups, and logical volumes. |

## Filesystem Management

| **Command**                        | **Description**                                                    |
|------------------------------------|--------------------------------------------------------------------|
| `mount -t <fstype> <device> <dir>` | Mount a filesystem of type `<fstype>` to a directory.              |
| `umount <dir>`                     | Unmount the filesystem from the directory.                         |
| `tune2fs -l /dev/sdXn`             | Display filesystem parameters for ext2/ext3/ext4 filesystems.      |
| `xfs_info /mnt`                    | Display information about an XFS filesystem mounted at `/mnt`.     |
| `fsck /dev/sdXn`                   | Check and repair a filesystem on `/dev/sdXn`.                      |
| `mkfs.ext4 /dev/sdXn`              | Create an ext4 filesystem on `/dev/sdXn`.                          |
| `mkfs.xfs /dev/sdXn`               | Create an XFS filesystem on `/dev/sdXn`.                           |
| `mount -o remount,rw /dev/sdXn /mnt` | Remount a filesystem as read-write.                                |

## Swap Management

| **Command**                        | **Description**                                                    |
|------------------------------------|--------------------------------------------------------------------|
| `mkswap /dev/sdXn`                 | Create a swap area on `/dev/sdXn`.                                 |
| `swapon /dev/sdXn`                 | Enable swap on the specified partition or file.                    |
| `swapoff /dev/sdXn`                | Disable swap on the specified partition or file.                   |
| `free -m`                          | Display memory and swap usage in megabytes.                        |
| `swapon -s`                        | Display summary information about swap usage.                      |

## Auto-Mount Configuration

| **File**                           | **Description**                                                    |
|------------------------------------|--------------------------------------------------------------------|
| `/etc/fstab`                       | File containing static information about filesystems to be mounted at boot. |

### Example `/etc/fstab` Entry:
```bash
/dev/sda1   /mnt/data   ext4    defaults    0   2
```

### Explanation:
- **Disk and Partition Management**: Commands for handling disk partitions, filesystems, and mounting.
- **Logical Volume Management (LVM)**: Commands for creating, extending, and managing LVM volumes.
- **Filesystem Management**: Commands for working with filesystems, including mounting, creating, and checking.
- **Swap Management**: Commands for creating, enabling, and managing swap space.
- **Auto-Mount Configuration**: Guidance on configuring filesystems to be automatically mounted at boot via `/etc/fstab`.

# CentOS Enterprise Linux 7 Network Management Cheat Sheet

## Network Interface Management

| **Command**                             | **Description**                                                    |
|-----------------------------------------|--------------------------------------------------------------------|
| `ip addr show`                          | Display IP addresses and network interfaces.                       |
| `nmcli device status`                   | Show the status of all network devices.                            |
| `ifconfig`                              | Display or configure network interfaces (deprecated, use `ip`).    |
| `ip link set <interface> up/down`       | Enable or disable a network interface.                             |
| `nmcli connection up <connection-name>` | Bring up a network connection by name.                             |
| `nmcli connection down <connection-name>` | Bring down a network connection by name.                          |
| `ethtool <interface>`                   | Display or change Ethernet device settings.                        |
| `nmtui`                                 | Text-based user interface for network management.                  |

## IP Address Configuration

| **Command**                             | **Description**                                                    |
|-----------------------------------------|--------------------------------------------------------------------|
| `ip addr add <IP>/<netmask> dev <interface>` | Add an IP address to a network interface.                     |
| `ip addr del <IP>/<netmask> dev <interface>` | Remove an IP address from a network interface.                |
| `nmcli con mod <connection> ipv4.addresses "<IP>/<netmask>"` | Modify the IP address for a connection.                  |
| `nmcli con mod <connection> ipv4.gateway "<gateway>"` | Set the default gateway for a connection.                       |
| `nmcli con mod <connection> ipv4.dns "<DNS1> <DNS2>"` | Set DNS servers for a connection.                               |
| `nmcli con reload`                      | Reload all network configurations.                                |

## DNS Management

| **Command**                             | **Description**                                                    |
|-----------------------------------------|--------------------------------------------------------------------|
| `cat /etc/resolv.conf`                  | Display DNS server configuration.                                   |
| `nmcli dev show | grep DNS`             | Display DNS configuration for network interfaces.                   |
| `host <hostname>`                       | Resolve a hostname to an IP address.                                |
| `dig <domain>`                          | Query DNS information for a domain.                                 |
| `nslookup <domain>`                     | Query DNS information (deprecated, use `dig`).                      |

## Routing

| **Command**                             | **Description**                                                    |
|-----------------------------------------|--------------------------------------------------------------------|
| `ip route show`                         | Display the kernel routing table.                                   |
| `ip route add <network> via <gateway>`  | Add a new static route.                                             |
| `ip route del <network>`                | Delete a static route.                                              |
| `route -n`                              | Display routing table with numeric IP addresses.                    |
| `nmcli con mod <connection> ipv4.routes "<network>/<CIDR> <gateway>"` | Add a persistent static route to a connection.    |

## Firewall Management

| **Command**                             | **Description**                                                    |
|-----------------------------------------|--------------------------------------------------------------------|
| `firewall-cmd --state`                  | Check if the firewall is running.                                   |
| `firewall-cmd --list-all`               | List all active firewall rules.                                     |
| `firewall-cmd --add-service=<service>`  | Temporarily allow a service (e.g., HTTP, SSH).                      |
| `firewall-cmd --permanent --add-service=<service>` | Permanently allow a service.                           |
| `firewall-cmd --remove-service=<service>` | Temporarily remove a service.                                      |
| `firewall-cmd --reload`                 | Reload firewall rules to apply changes.                             |
| `firewall-cmd --list-ports`             | List all open ports in the firewall.                                |
| `firewall-cmd --add-port=<port>/tcp --permanent` | Open a specific port permanently (e.g., `8080/tcp`).               |

## Network Diagnostics

| **Command**                             | **Description**                                                    |
|-----------------------------------------|--------------------------------------------------------------------|
| `ping <host>`                           | Test network connectivity to a host.                                |
| `traceroute <host>`                     | Trace the route packets take to a host.                             |
| `mtr <host>`                            | Real-time network diagnostics tool combining `ping` and `traceroute`. |
| `netstat -tuln`                         | Display listening ports and their services.                         |
| `ss -tuln`                              | Display listening sockets (replacement for `netstat`).              |
| `tcpdump -i <interface>`                | Capture network packets on a specified interface.                   |
| `nmcli dev status`                      | Show the status of network devices.                                 |
| `nmcli con show`                        | List all active and inactive network connections.                   |

## Network Services

| **Command**                             | **Description**                                                    |
|-----------------------------------------|--------------------------------------------------------------------|
| `systemctl start/stop/restart network`  | Start, stop, or restart the network service.                        |
| `systemctl enable/disable network`      | Enable or disable the network service at boot.                      |
| `systemctl status network`              | Check the status of the network service.                            |
| `systemctl restart NetworkManager`      | Restart the NetworkManager service.                                 |
| `systemctl enable/disable NetworkManager` | Enable or disable NetworkManager at boot.                         |
| `systemctl status NetworkManager`       | Check the status of the NetworkManager service.                     |

## VPN Configuration

| **Command**                             | **Description**                                                    |
|-----------------------------------------|--------------------------------------------------------------------|
| `nmcli connection import type openvpn file <file.ovpn>` | Import an OpenVPN configuration file.                    |
| `nmcli connection up <vpn-connection>`  | Connect to a VPN.                                                  |
| `nmcli connection down <vpn-connection>` | Disconnect from a VPN.                                            |
| `nmcli con mod <vpn-connection> vpn.data "key=value"` | Modify VPN settings.                                 |
| `ipsec status`                          | Check the status of IPsec VPN connections.                          |

## Network Interface Bonding

| **Command**                             | **Description**                                                    |
|-----------------------------------------|--------------------------------------------------------------------|
| `nmcli con add type bond ifname bond0 mode active-backup` | Create a bond interface with active-backup mode.    |
| `nmcli con add type bond-slave ifname eth0 master bond0` | Add a slave interface to a bond.                     |
| `nmcli con mod bond0 ipv4.addresses "192.168.1.100/24"` | Assign an IP address to the bond interface.          |
| `nmcli con up bond0`                    | Bring up the bond interface.                                      |
| `cat /proc/net/bonding/bond0`           | Display the status of the bond interface.                         |

## Network Time Protocol (NTP)

| **Command**                             | **Description**                                                    |
|-----------------------------------------|--------------------------------------------------------------------|
| `timedatectl`                           | Display or set the system date and time.                            |
| `timedatectl set-ntp true`              | Enable NTP synchronization.                                         |
| `ntpdate <ntp-server>`                  | Synchronize the system clock with an NTP server.                    |
| `chronyc sources`                       | Display the current NTP sources.                                    |
| `systemctl restart chronyd`             | Restart the chrony service.                                         |
| `systemctl enable chronyd`              | Enable the chrony service at boot.                                  |


# CentOS Enterprise Linux 7 Service Management Cheat Sheet

## Basic Service Commands

| **Command**                            | **Description**                                                    |
|----------------------------------------|--------------------------------------------------------------------|
| `systemctl start <service>`            | Start a service.                                                   |
| `systemctl stop <service>`             | Stop a service.                                                    |
| `systemctl restart <service>`          | Restart a service.                                                 |
| `systemctl reload <service>`           | Reload a service's configuration without stopping it.              |
| `systemctl enable <service>`           | Enable a service to start at boot.                                 |
| `systemctl disable <service>`          | Disable a service from starting at boot.                           |
| `systemctl status <service>`           | Check the status of a service.                                      |
| `systemctl is-active <service>`        | Check if a service is currently active.                            |
| `systemctl is-enabled <service>`       | Check if a service is enabled to start at boot.                    |
| `systemctl list-units --type=service`  | List all active services.                                          |
| `systemctl list-unit-files --type=service` | List all installed service unit files.                          |

## Managing Systemd Units

| **Command**                            | **Description**                                                    |
|----------------------------------------|--------------------------------------------------------------------|
| `systemctl daemon-reload`              | Reload systemd manager configuration after a unit file change.     |
| `systemctl cat <service>`              | Display the content of a service's unit file.                      |
| `systemctl edit <service>`             | Edit a service's unit file (opens in default editor).              |
| `systemctl show <service>`             | Show properties of a service unit.                                 |
| `journalctl -u <service>`              | View logs for a specific service.                                  |
| `systemctl mask <service>`             | Prevent a service from being started, manually or automatically.   |
| `systemctl unmask <service>`           | Unmask a service to allow it to start.                             |
| `systemctl link /path/to/custom.service` | Link a custom unit file into `/etc/systemd/system/`.              |

## Service Logs and Debugging

| **Command**                            | **Description**                                                    |
|----------------------------------------|--------------------------------------------------------------------|
| `journalctl -xe`                       | View the system journal (logs) with detailed errors and messages.  |
| `journalctl -u <service> -b`           | View logs for a service since the last boot.                       |
| `journalctl --since "YYYY-MM-DD HH:MM:SS"` | View logs since a specific date and time.                       |
| `journalctl --no-pager`                | View the entire log without paging.                                |
| `systemctl --failed`                   | List all failed services and units.                                |

## Service Target Management

| **Command**                            | **Description**                                                    |
|----------------------------------------|--------------------------------------------------------------------|
| `systemctl get-default`                | Display the default target (runlevel).                             |
| `systemctl set-default <target>`       | Set the default target (e.g., `multi-user.target`, `graphical.target`). |
| `systemctl isolate <target>`           | Change to a specific target immediately (e.g., `rescue.target`).   |
| `systemctl list-dependencies <target>` | List all dependencies of a target.                                 |
| `systemctl rescue`                     | Switch to rescue mode (single-user mode with minimal services).    |
| `systemctl emergency`                  | Switch to emergency mode (maintenance mode with only essential services). |

## Custom Service Management

| **Command**                            | **Description**                                                    |
|----------------------------------------|--------------------------------------------------------------------|
| `nano /etc/systemd/system/<name>.service` | Create or edit a custom service unit file.                      |
| `[Unit]`                                | Section of the unit file containing metadata and dependencies.   |
| `[Service]`                             | Section of the unit file describing the service behavior.        |
| `[Install]`                             | Section of the unit file containing installation information (e.g., wanted by target). |
| `systemctl daemon-reload`              | Reload systemd configuration after creating/editing a unit file.  |
| `systemctl start <name>.service`       | Start the custom service.                                          |
| `systemctl enable <name>.service`      | Enable the custom service to start at boot.                        |

## Legacy Service Management (SysVinit)

| **Command**                            | **Description**                                                    |
|----------------------------------------|--------------------------------------------------------------------|
| `service <service> start`              | Start a service using the SysVinit method.                         |
| `service <service> stop`               | Stop a service using the SysVinit method.                          |
| `service <service> restart`            | Restart a service using the SysVinit method.                       |
| `service <service> status`             | Check the status of a service using the SysVinit method.           |
| `chkconfig <service> on`               | Enable a SysVinit service to start at boot.                        |
| `chkconfig <service> off`              | Disable a SysVinit service from starting at boot.                  |
| `chkconfig --list <service>`           | List the runlevels for a SysVinit service.                         |
| `/etc/init.d/<service> start`          | Start a service directly from its init script.                     |

# CentOS Enterprise Linux 7 Virtualization Management Cheat Sheet

## KVM Installation and Setup

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `yum install qemu-kvm libvirt virt-install bridge-utils` | Install KVM and related packages.                            |
| `systemctl start libvirtd`                       | Start the libvirtd service.                                        |
| `systemctl enable libvirtd`                      | Enable the libvirtd service to start at boot.                      |
| `virsh list --all`                               | List all virtual machines (VMs).                                   |
| `virt-manager`                                   | Launch the Virtual Machine Manager graphical interface.            |
| `virt-install --name <vm_name> --memory <size> --vcpus <num> --disk <path>,size=<size> --cdrom <iso>` | Create and install a new VM. |

## Managing Virtual Machines

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `virsh start <vm_name>`                          | Start a virtual machine.                                           |
| `virsh shutdown <vm_name>`                       | Shut down a virtual machine.                                       |
| `virsh reboot <vm_name>`                         | Reboot a virtual machine.                                          |
| `virsh destroy <vm_name>`                        | Forcefully stop a virtual machine.                                 |
| `virsh suspend <vm_name>`                        | Suspend a virtual machine.                                         |
| `virsh resume <vm_name>`                         | Resume a suspended virtual machine.                                |
| `virsh autostart <vm_name>`                      | Enable a VM to start automatically at host boot.                   |
| `virsh autostart --disable <vm_name>`            | Disable a VM from starting automatically at host boot.             |
| `virsh undefine <vm_name>`                       | Delete a VM definition.                                            |
| `virsh console <vm_name>`                        | Access the console of a running VM.                                |

## Storage Management

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `virsh pool-list`                                | List all storage pools.                                            |
| `virsh pool-create <pool_xml>`                   | Create a new storage pool from an XML file.                        |
| `virsh pool-start <pool_name>`                   | Start a storage pool.                                              |
| `virsh pool-destroy <pool_name>`                 | Destroy a storage pool (stop it without removing it).              |
| `virsh pool-define-as <name> <type> --target <path>` | Define a new storage pool.                                      |
| `virsh pool-delete <pool_name>`                  | Delete a storage pool (removes all storage volumes).               |
| `virsh vol-list <pool_name>`                     | List all volumes in a storage pool.                                |
| `virsh vol-create-as <pool_name> <vol_name> <size>` | Create a new storage volume in a pool.                          |
| `virsh vol-delete <vol_name> --pool <pool_name>` | Delete a storage volume.                                           |
| `virsh vol-info <vol_name> --pool <pool_name>`   | Show detailed information about a storage volume.                  |

## Network Management

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `virsh net-list --all`                           | List all virtual networks.                                         |
| `virsh net-create <network_xml>`                 | Create a new virtual network from an XML file.                     |
| `virsh net-start <network_name>`                 | Start a virtual network.                                           |
| `virsh net-destroy <network_name>`               | Destroy (stop) a virtual network.                                  |
| `virsh net-autostart <network_name>`             | Enable a virtual network to start automatically at host boot.      |
| `virsh net-undefine <network_name>`              | Delete a virtual network definition.                               |
| `virsh net-edit <network_name>`                  | Edit a virtual network configuration.                              |
| `virsh net-info <network_name>`                  | Display information about a virtual network.                       |
| `virsh iface-list`                               | List all physical network interfaces on the host.                  |
| `virsh iface-start <interface_name>`             | Start a network interface.                                         |
| `virsh iface-destroy <interface_name>`           | Destroy (stop) a network interface.                                |

## Snapshots and Backups

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `virsh snapshot-list <vm_name>`                  | List all snapshots for a VM.                                       |
| `virsh snapshot-create-as <vm_name> <snapshot_name>` | Create a snapshot for a VM.                                      |
| `virsh snapshot-revert <vm_name> <snapshot_name>` | Revert a VM to a specific snapshot.                               |
| `virsh snapshot-delete <vm_name> <snapshot_name>` | Delete a snapshot.                                                |
| `virsh dumpxml <vm_name> > <path>.xml`           | Backup a VM's configuration to an XML file.                       |
| `virsh define <path>.xml`                        | Restore a VM's configuration from an XML file.                    |
| `virsh vol-clone <source_vol> <dest_vol> --pool <pool_name>` | Clone a storage volume to create a backup.                     |

## Resource Allocation and Tuning

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `virsh setmem <vm_name> <size> --config`         | Set the maximum memory allocation for a VM.                        |
| `virsh setvcpus <vm_name> <num> --config`        | Set the number of virtual CPUs for a VM.                           |
| `virsh blkiotune <vm_name> --weight <weight>`    | Set the block I/O weight for a VM.                                 |
| `virsh schedinfo <vm_name>`                      | Display or set scheduling parameters for a VM.                     |
| `virsh setmaxmem <vm_name> <size> --config`      | Set the maximum amount of memory that a VM can use.                |
| `virsh vcpuinfo <vm_name>`                       | Display detailed information about the VCPUs of a VM.              |

## Miscellaneous

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `virt-clone --original <vm_name> --name <new_vm_name> --file <path>` | Clone an existing VM.                                          |
| `virt-top`                                       | Monitor virtual machine resources (similar to `top` command).       |
| `virt-sysprep -d <vm_name>`                      | Prepare a VM for cloning by removing sensitive data.               |
| `virt-resize --expand /dev/sda1 <source.img> <dest.img>` | Resize a VM disk image.                                      |
| `virt-customize -a <disk.img> --run-command 'yum update -y'` | Customize a VM disk image.                                    |


# Debian Software Management Cheat Sheet

## Basic Package Management with APT

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `sudo apt-get update`                            | Update the package list from repositories.                         |
| `sudo apt-get upgrade`                           | Upgrade all installed packages to their latest versions.           |
| `sudo apt-get dist-upgrade`                      | Upgrade packages, handling dependencies intelligently.             |
| `sudo apt-get install <package>`                 | Install a package.                                                 |
| `sudo apt-get remove <package>`                  | Remove a package but keep its configuration files.                 |
| `sudo apt-get purge <package>`                   | Remove a package along with its configuration files.               |
| `sudo apt-get autoremove`                        | Remove unnecessary packages that were automatically installed.     |
| `sudo apt-get clean`                             | Clean up the local repository of retrieved package files.          |
| `sudo apt-cache search <keyword>`                | Search for a package by keyword.                                   |
| `sudo apt-cache show <package>`                  | Display detailed information about a package.                      |

## Working with Repositories

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `sudo add-apt-repository <repository>`           | Add a new repository to the sources list.                          |
| `sudo apt-add-repository ppa:<repository>`       | Add a Personal Package Archive (PPA) repository.                   |
| `sudo apt-get update`                            | Update the package list after adding a new repository.             |
| `sudo apt-key add <keyfile>`                     | Add a repository’s GPG key from a file.                            |
| `sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <key>` | Add a repository’s GPG key using a keyserver.          |
| `/etc/apt/sources.list`                          | Main configuration file for APT repositories.                      |
| `/etc/apt/sources.list.d/`                       | Directory for additional repository list files.                    |

## Package Information and Management

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `dpkg -l`                                        | List all installed packages.                                       |
| `dpkg -s <package>`                              | Display the status of a package (installed or not).                |
| `dpkg -L <package>`                              | List the files installed by a package.                             |
| `dpkg -I <package.deb>`                          | Display information about a `.deb` package file.                   |
| `dpkg -i <package.deb>`                          | Install a package from a `.deb` file.                              |
| `dpkg -r <package>`                              | Remove a package but keep its configuration files.                 |
| `dpkg --purge <package>`                         | Remove a package along with its configuration files.               |
| `dpkg-reconfigure <package>`                     | Reconfigure an already installed package.                          |

## Advanced APT Usage

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `sudo apt-mark hold <package>`                   | Hold a package back from being upgraded.                           |
| `sudo apt-mark unhold <package>`                 | Remove a hold on a package to allow it to be upgraded.             |
| `sudo apt-cache policy <package>`                | Show installed and available versions of a package.                |
| `sudo apt-get source <package>`                  | Download the source code of a package.                             |
| `sudo apt-get build-dep <package>`               | Install build dependencies for a package.                          |
| `sudo apt-get check`                             | Check for broken dependencies.                                     |
| `sudo apt-get -f install`                        | Fix broken dependencies by attempting to correct them.             |

## Package Pinning and Preferences

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `/etc/apt/preferences`                           | File for configuring package pinning (priority-based version selection). |
| `/etc/apt/preferences.d/`                        | Directory for additional preferences files.                        |
| `Pin: release a=stable`                          | Example preference to pin a package to the stable release.         |
| `Pin-Priority: 1001`                             | Example pin priority to force installation of a specific version.  |

## Troubleshooting and Logs

| **Command**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `/var/log/apt/history.log`                       | Log file for APT operations and history.                           |
| `/var/log/apt/term.log`                          | Log file for terminal output of APT commands.                      |
| `sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade` | Debug package resolution problems during upgrade.       |
| `sudo dpkg --configure -a`                       | Reconfigure any partially installed packages.                      |
| `sudo apt-get install -f`                        | Attempt to fix broken dependencies.                                |


# Creating Shell Scripts in Enterprise Linux Cheat Sheet

## Script Basics

| **Concept**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `#!/bin/bash`                                     | Shebang line to specify the script interpreter (Bash).             |
| `chmod +x script.sh`                              | Make the script executable.                                        |
| `./script.sh`                                     | Run the script from the current directory.                         |
| `bash script.sh`                                  | Execute the script using the Bash shell.                           |
| `sh script.sh`                                    | Execute the script using the default shell.                        |
| `set -e`                                          | Exit the script immediately if any command fails.                  |
| `set -x`                                          | Print each command before executing it (useful for debugging).     |

## Variables

| **Concept**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `VAR=value`                                      | Define a variable.                                                 |
| `echo $VAR`                                      | Access the value of a variable.                                    |
| `VAR=$(command)`                                 | Assign the output of a command to a variable.                      |
| `readonly VAR=value`                             | Declare a variable as read-only.                                   |
| `unset VAR`                                      | Unset or delete a variable.                                        |

## Input and Output

| **Concept**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `read VAR`                                       | Read input from the user into a variable.                          |
| `echo "Hello, World!"`                           | Print text to the terminal.                                        |
| `echo -e "Line1\nLine2"`                         | Print text with newlines or special characters.                    |
| `echo -n "No newline"`                           | Print text without adding a newline at the end.                    |
| `cat file.txt`                                   | Display the contents of a file.                                    |
| `command > file.txt`                             | Redirect output of a command to a file, overwriting the file.      |
| `command >> file.txt`                            | Append the output of a command to a file.                          |

## Conditional Statements

| **Concept**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `if [ condition ]; then ... fi`                  | Basic `if` statement.                                              |
| `if [ condition ]; then ... else ... fi`         | `if-else` statement.                                               |
| `if [ condition1 ]; then ... elif [ condition2 ]; then ... fi` | `if-elif-else` statement.                      |
| `test condition`                                 | Use `test` command to evaluate a condition.                        |
| `[[ condition ]]`                                | Advanced conditional expression.                                   |
| `case $VAR in pattern1) commands ;; pattern2) commands ;; esac` | `case` statement for multiple conditions.  |

## Loops

| **Concept**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `for VAR in list; do ... done`                   | Iterate over a list of values.                                     |
| `while [ condition ]; do ... done`               | Repeat a block of commands while a condition is true.              |
| `until [ condition ]; do ... done`               | Repeat a block of commands until a condition becomes true.         |
| `break`                                          | Exit a loop immediately.                                           |
| `continue`                                       | Skip the current iteration and proceed to the next one.            |

## Functions

| **Concept**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `function name { commands; }`                    | Define a function.                                                 |
| `name`                                           | Call a function.                                                   |
| `name arg1 arg2`                                 | Call a function with arguments.                                    |
| `$1, $2, ...`                                    | Access positional parameters within a function or script.          |
| `return value`                                   | Return a value from a function.                                    |

## Error Handling

| **Concept**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `exit 0`                                         | Exit the script with a success status (0).                         |
| `exit 1`                                         | Exit the script with an error status (non-zero).                   |
| `trap 'commands' EXIT`                           | Execute commands on script exit.                                   |
| `trap 'commands' ERR`                            | Execute commands when an error occurs.                             |
| `command || { echo "Error"; exit 1; }`           | Run a command and handle errors.                                   |

## Script Arguments

| **Concept**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `$0`                                             | The name of the script being executed.                             |
| `$1, $2, ...`                                    | Positional parameters passed to the script.                        |
| `$@`                                             | All the arguments passed to the script.                            |
| `$#`                                             | The number of arguments passed to the script.                      |
| `shift`                                          | Shift positional parameters to the left.                           |

## File Operations

| **Concept**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `touch filename`                                 | Create an empty file or update its timestamp.                      |
| `rm filename`                                    | Delete a file.                                                     |
| `cp source destination`                          | Copy a file or directory.                                          |
| `mv source destination`                          | Move or rename a file or directory.                                |
| `find /path -name "pattern"`                     | Find files or directories by name.                                 |
| `grep "pattern" file.txt`                        | Search for a pattern within a file.                                |

## Debugging and Optimization

| **Concept**                                      | **Description**                                                    |
|--------------------------------------------------|--------------------------------------------------------------------|
| `bash -x script.sh`                              | Execute a script in debug mode (print each command).               |
| `bash -n script.sh`                              | Check the script for syntax errors without executing it.           |
| `time command`                                   | Measure the time taken to execute a command.                       |
| `exec > logfile 2>&1`                            | Redirect all script output to a file, including errors.            |
| `set +x`                                         | Disable debug mode in a script.                                    |




