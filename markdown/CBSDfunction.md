# CBSD Commands by Function

This document organizes CBSD commands by their primary functions and use cases.

## Virtualization Management

### Bhyve VM Operations
- `bcreate` - Create new bhyve VM
- `bstart` - Start bhyve VM
- `bstop` - Stop bhyve VM
- `brestart` - Restart bhyve VM
- `bremove` - Remove bhyve VM
- `bls` - List bhyve VMs
- `blogin` - Login to bhyve VM
- `bexec` - Execute command in VM
- `bclone` - Clone bhyve VM
- `bmigrate` - Perform live migration
- `bcheckpoint` - Create VM checkpoint
- `bpause` - Pause/resume VM
- `brenice` - Adjust VM process priority

### Bhyve Storage Management
- `bhyve-controller` - Manage storage controllers
- `bhyve-dsk` - Manage AHCI/virtio disks
- `bhyve-nvme` - Manage NVMe storage
- `bhyve-p9shares` - Manage 9P shared folders
- `vhidcfg` - Manage disk images

### Bhyve Network Management
- `bhyve-nic` - Manage network interfaces
- `valecfg` - Configure VALE switches
- `vpc` - Manage VPC networks

### Bhyve Configuration
- `bconfig` - Configure VM settings
- `bset` - Modify VM parameters
- `bconstruct-tui` - VM creation wizard
- `bcontrol-tui` - VM control interface
- `vm-cpu-topology` - Configure CPU topology

## Jail Management

### Basic Jail Operations
- `jcreate` - Create new jail
- `jstart` - Start jail
- `jstop` - Stop jail
- `jrestart` - Restart jail
- `jremove` - Remove jail
- `jls` - List jails
- `jlogin` - Login to jail
- `jexec` - Execute command in jail
- `jclone` - Clone jail
- `jimport` - Import jail from image
- `jexport` - Export jail to image

### Jail Configuration
- `jconfig` - Configure jail settings
- `jset` - Modify jail parameters
- `jrctl` - Set resource limits
- `jsnapshot` - Manage snapshots
- `jrctl-tui` - Resource control interface
- `jsetup-tui` - Jail setup interface

### Jail Networking
- `expose` - Configure port forwarding
- `natcfg` - Configure NAT
- `naton/natoff` - Enable/disable NAT

## System Management

### Base System
- `initenv` - Initialize CBSD environment
- `baseupdate` - Update base system
- `srcup` - Update source tree
- `upgrade` - Upgrade CBSD
- `bases` - Show base jails
- `kernels` - Show kernels
- `sources` - Show sources

### Build Operations
- `buildworld` - Build FreeBSD world
- `buildkernel` - Build kernel
- `installworld` - Install world
- `installkernel` - Install kernel
- `distribution` - Create distribution

### Storage Operations
- `zfs` - ZFS operations
- `geli` - Encryption operations
- `media` - Manage storage media
- `images` - Manage images
- `zfs-migrator` - Migrate ZFS datasets

## Network Management

### Network Configuration
- `natcfg` - NAT configuration
- `vpc` - VPC management
- `bridge` - Bridge management
- `vnet` - VNET configuration

### Network Tools
- `dhcpd` - DHCP management
- `checkip` - IP address verification
- `getip-by-nics` - Get IPs from interfaces
- `getnics-by-ip` - Get interfaces from IP

## Node Management

### Node Operations
- `node` - Node management
- `nlogin` - Remote node login
- `nodescp` - Copy files between nodes
- `nodeaddkey` - Add node SSH keys

### Node Information
- `ndescr` - Node description
- `netinv` - Network inventory
- `sysinv` - System inventory
- `mkinventory` - Create inventory

## Service Management

### Service Control
- `service` - Service management
- `forms` - Service configuration
- `puppet` - Puppet integration
- `srvbrowser-tui` - Service browser

### Package Management
- `pkg` - Package management
- `pkgbrowser` - Package browser
- `portsup` - Ports tree update

## Task Management

### Task Operations
- `task` - Task management
- `taskls` - List tasks
- `nexttask` - Execute next task
- `cbsdd` - Task daemon

## Security Management

### Access Control
- `rctl` - Resource control
- `cpuset` - CPU set management
- `adduser` - User management
- `userlist` - List users
- `grouplist` - List groups

### Security Tools
- `sshkey` - SSH key management
- `secretsfile` - Generate secrets
- `geli` - Disk encryption

## Monitoring and Statistics

### System Monitoring
- `summary` - System summary
- `sockstat` - Socket statistics
- `trafstat` - Traffic statistics
- `fwcounters` - Firewall counters
- `rctlcounters` - Resource counters

## Utility Commands

### File Operations
- `bscp` - Copy files to/from VM
- `nodescp` - Copy files between nodes
- `mountfstab` - Mount filesystems
- `unmountfstab` - Unmount filesystems

### Helper Tools
- `freejname` - Suggest environment names
- `freectr` - Suggest controller names
- `help` - Show help
- `history` - Command history

## Notes

### Command Categories
- [bhyve] - Bhyve virtualization
- [jail] - Jail management
- [sys] - System operations
- [build] - Build utilities
- [bsdconf] - BSD configuration
- [taskd] - Task management

### Usage
```sh
cbsd <command> [options]
cbsd help <command>
``` 