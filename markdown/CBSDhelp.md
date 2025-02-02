# CBSD Help System

CBSD provides a comprehensive help system that can be accessed through various commands. This document outlines the available help commands and their usage.

## Basic Help Commands

### General Help
```sh
cbsd help
```
Shows general CBSD usage and available command categories.

### Command-Specific Help
```sh
cbsd help <command>
```
Shows detailed help for a specific command.

## Command Categories

### Virtual Machine Management (bhyve)
- `bcreate` - Create bhyve VM from config file or args
- `bstart` - Start bhyve domain
- `bstop` - Stop bhyve domain
- `bremove` - Remove bhyve VM
- `bls` - List bhyve domains and status
- `bconfig` - Modify parameters for bhyve domain (interactive/dialog)
- `blogin` - Execute login into VM
- `bexec` - Execute command inside cloud-based VM
- `bclone` - Clone bhyve VM
- `bmigrate` - Perform live migration
- `bcheckpoint` - Create bhyve checkpoint
- `brestart` - Perform bstop/bstart sequence

#### Storage Management
- `bhyve-controller` - Manage bhyve controller
- `bhyve-dsk` - Manage bhyve AHCI/virtio disks
- `bhyve-nvme` - Manage bhyve NVMe storage
- `bhyve-p9shares` - Manage 9P shared folders

#### Network Management
- `bhyve-nic` - Operate with bhyve NICs
- `valecfg` - Manage virtual VALE switch

### Jail Management
- `jcreate` - Create jail from config file or args
- `jstart` - Start jail
- `jstop` - Stop jail
- `jremove` - Remove jail
- `jls` - List jails and status
- `jconfig` - Configure jail settings
- `jexec` - Execute command inside jail
- `jlogin` - Login to jail
- `jclone` - Clone jail
- `jsnapshot` - Manage jail snapshots
- `jupgrade` - Upgrade jail base data
- `jrctl` - Set resource limits

### System Management
- `initenv` - Initialize CBSD environment
- `baseupdate` - Update base system
- `srcup` - Update source tree
- `upgrade` - Upgrade CBSD
- `bases` - Show registered basejails
- `kernels` - Show BSD kernels
- `sources` - Show BSD sources

### Network Management
- `natcfg` - Configure NAT service
- `naton` - Enable NAT for RFC1918 networks
- `natoff` - Disable NAT service
- `vpc` - Manage VXLAN-based multi-node networks

### Storage Management
- `zfs` - ZFS operations
- `geli` - GELI encryption helper
- `media` - Manage virtual storage media
- `images` - Manage environment images

### Container Management
- `forms` - Work with configuration forms
- `puppet` - Puppet integration
- `rctl` - Resource controls
- `repo` - Repository operations

### Node Management
- `node` - Manage remote nodes
- `nlogin` - Login to remote node
- `nodescp` - Copy files to/from remote nodes

## Common Usage Examples

### Virtual Machine Operations
```sh
# Create new VM
cbsd bcreate vm_name="myvm" vm_os_type="freebsd" vm_os_profile="FreeBSD-x64-14.2"

# Configure VM storage
cbsd bhyve-dsk mode=attach name=myvm dsk_path=/dev/zvol/zroot/vm1

# Configure VM network
cbsd bhyve-nic mode=attach name=myvm nic_parent=bridge0

# Start VM
cbsd bstart myvm
```

### Jail Operations
```sh
# Create new jail
cbsd jcreate jname="myjail" host_hostname="myjail.local"

# Set resource limits
cbsd jrctl mode=set jname=myjail memoryuse=1g

# Start jail
cbsd jstart myjail

# Execute command in jail
cbsd jexec jname=myjail cmd="pkg install nginx"
```

### Network Operations
```sh
# Configure NAT
cbsd natcfg mode=configure

# Create VPC network
cbsd vpc mode=create name=vpc1 network=10.0.0.0/16
```

## Help Topics

### Configuration
- Environment setup
- Network configuration
- Storage configuration
- Resource limits

### Security
- Jail security
- Network isolation
- Resource controls
- Access controls

### Maintenance
- Backups
- Updates
- Migrations
- Health checks

## Notes

1. **Command Structure**:
   - All commands start with `cbsd`
   - Most commands have short and long forms
   - Many commands accept multiple parameters

2. **Help Format**:
   - Synopsis shows command usage
   - Description explains command purpose
   - Parameters list available options
   - Examples show common usage

3. **Documentation**:
   - Online documentation available
   - Man pages for most commands
   - Wiki with additional examples
   - Community forums for support

4. **Best Practices**:
   - Check help before using new commands
   - Test commands in development first
   - Use resource limits appropriately
   - Keep CBSD updated 

## Complete Command Reference

### A
- `adduser` - [jail] Manage user and password in jail/chroot environment
- `adduser-tui` - [bsdconf] Ncurses based dialog for adduser
- `apply` - [bhyve,jail] apply/re-configure virtual environment via CBSDfile
- `attachgeli` - [sys] Mount GELI-based image
- `attachzfs` - [jail] Delegate ZFS filesystem to jail

### B
- `bases` - [jail,sys] Show registered basejail for jails
- `baseupdate` - [sys] Update base jail
- `bcheckpoint` - [bhyve] bhyve checkpoint
- `bchroot` - [bhyve,sys] Drop bhyve domain into jail
- `bcleanup` - [bhyve] Force cleanup bhyve VM-related stuff (e.g. nics)
- `bclone` - [bhyve] bhyve cloning
- `bconfig` - [bhyve] Modify parameters for bhyve domain (interactive/dialog)
- `bconstruct-tui` - [bhyve] Ncurses based bhyve guest creation wizard
- `bcontrol-tui` - [bhyve] Ncurses based control for bhyve
- `bcreate` - [bhyve] Create bhyve VM from config file or args
- `bdescr` - [bhyve] Show or modify jail description
- `bdestroy` - [bhyve] Destroy bhyve domain
- `bexec` - [bhyve] Execution for command inside cloud-based vm
- `bget` - [bhyve] Get info related to bhyve domain
- `bhyve-controller` - [bhyve] Manage bhyve controller
- `bhyve-controller-list` - [bhyve] Show bhyve storage controller
- `bhyve-controller-tui` - [bhyve] TUI for bhyve storage controller
- `bhyve-dsk` - [bhyve] Manage bhyve ahci/virtio disk
- `bhyve-dsk-list` - [bhyve] Show bhyve disks
- `bhyve-dsk-tui` - [bhyve] TUI for bhyve disk management
- `bhyve-exist` - [bhyve] Check if bhyve process exists
- `bhyve-nic` - [bhyve] Operate with bhyve NICs
- `bhyve-nic-list` - [bhyve] Shows bhyve NICs
- `bhyve-nic-tui` - [bhyve] Dialog based UI to manage bhyve NIC
- `bhyve-nvme` - [bhyve] Manage bhyve NVMe storage controller
- `bhyve-nvme-list` - [bhyve] Show bhyve NVMe storage controller
- `bhyve-nvme-tui` - [bhyve] TUI for bhyve NVMe storage controller
- `bhyve-p9shares` - [bhyve] Manage bhyve 9P shared folders
- `bhyve-ppt` - [bhyve] Manage bhyve ppt devices
- `bjail` - [bhyve] Drop bhyve domain into jail
- `blogin` - [bhyve] Exec login into jail
- `bls` - [bhyve] List bhyve domain and status
- `bmigrate` - [bhyve] bhyve live migration
- `bootmgmt` - Choose and return boot device
- `bootmgmt-pxe` - Choose and return boot device
- `border` - [bhyve] List bhyve run order
- `border-tui` - [bhyve] Ncurses based bhyve order editor
- `bpause` - [bhyve] Pause and resume bhyve domain
- `bpcibus` - [bhyve] Operate with bhyve PCI bus map
- `brctl-tui` - [bhyve] Dialog based UI for RACCR/RCTL
- `brename` - [bhyve] Rename bhyve
- `brenice` - [bhyve] Re-nice bhyve processes on-the-fly
- `brestart` - [bhyve] bhyve bstop bstart sequence
- `bscp` - [bhyve] copy files from/to VM via scp(1)
- `bset` - [bhyve] Modify parameters for bhyve domain
- `bsetup-tui` - [bhyve] dialog-based text user interface for bhyve VM configuration
- `bstart` - [bhyve] Start bhyve domain
- `bstop` - [bhyve] Stop bhyve domain
- `bswmode` - [bhyve] switch environment mode between master/slave
- `buildkernel` - [build] Build kernel from sources
- `buildworld` - [sys] Build FreeBSD world from sources (basejail)

### C
- `capabilities` - [sys] Show CBSD capabilities for current platform
- `carpcfg` - Enable CARP configuration
- `carpcontrol` - Carp action collector
- `cbsdchown` - Chown for rc.conf/fstab/system directory to cbsd user
- `cbsdd` - [taskd] Daemon for executing nexttask
- `check_for_empty_hdd` - Check if virtual disk with no data/empty
- `checkip` - Check for IP exist or in pool
- `checkrhost` - Check availability of remote node
- `cloudinit` - [sys] cloud-init helper to generate CI yaml
- `copy-binlib` - [sys] Copy files by index file from basedir to dstdir
- `cpu-topology` - [sys] Show cpu topology
- `cpuset` - [bhyve,jail] show cpuset info

### D
- `delete-old-libs` - [sys] delete obsolete directories/files in bases/jails
- `destroy` - [bhyve,jail] destroy jail/bhyve env from CBSDfile
- `detachzfs` - Undelegate ZFS filesystem from jail
- `dhcpd` - Detect first available IPv4 from pools
- `dhcpdv6` - Detect first available IPv6 from pools
- `disks-list` - Return for visible storage
- `distccmakeconf` - put into copy of original make.conf specific distcc records
- `distribution` - [build] make distribution for FreeBSD base

### E
- `etcupdate` - [jail] etcupdate helper, manage updates to system files
- `expose` - [bhyve,jail] Exposing a port (port forwarding) to env via IPFW or PF

### F
- `fetch_iso` - [sys] Fetch ISO images from mirror sites
- `forms` - [jail] Assistant for configuring containers/services, TUI/CLI
- `freectr` - [bhyve] Suggest first free bhyve controller name
- `freejname` - [bhyve,jail] Suggest first free available environment name
- `ftp` - [bsdconf] Install timezone helper
- `fwcounters` - Collect IPFW count for virtual env if available

### G
- `geli` - cbsd geli helper
- `get-next-ng-port` - [bhyve] get next free NETGRAPH port
- `get-next-tcp-port` - scan port via nc to determine first available tcp port
- `get-next-vale-port` - [bhyve] get next free VALE port
- `get-profiles` - [bhyve,jail,xen] list of available profiles
- `getinfo` - Get information from node registry
- `getip-by-nics` - Return first IPv4 on specified interface
- `getnics-by-ip` - Return network interface name by IP
- `grouplist` - Show group list

### H-I
- `help` - [sys] This help
- `history` - [sys] Show cbsd history command
- `images` - [sys] Manage environment images
- `imghelper-tui` - Ncurses-based jail image bootstrap helper
- `imgpart` - Pack or extract chunk from image
- `imgremove` - [sys] Remove CBSD image from directory
- `imgtype` - [sys] Show image type: iso or vhd or ..
- `initenv` - [sys] Node re-initialization
- `install-pkg-world` - [sys] Install base-in-package FreeBSD base
- `installkernel` - [build] Install kernel from sources
- `installworld` - [sys] Install base from obj files after buildworld

### J
- `jail2iso` - Create bootable ISO/Memstick/MFSBSD image from CBSD jail
- `jailmapdb` - Return or update node for jail map in ASCII file
- `jbackup` - Backup jail to slave node with slave status
- `jcoldmigrate` - [jail] Cold migrate jail to remote node
- `jgensecrets` - Generate jail secrets phrase sequence for rsync
- `jimport` - [jail] Import jail from image
- `jmkrcconf` - [jail] Create ascii rc.conf for jail
- `jmkrctlconf` - [jail] Import/export rctl.conf from/to SQLite3

### K
- `k8hetzner2` - [sys] Operate with K8S cluster
- `k8s` - [sys] Operate with K8S cluster
- `k8world` - [sys] Operate with K8S cluster
- `kernels` - [sys] Show BSD kernels

### L-M
- `logger` - Log CBSD events
- `make_tmp_helper` - Copy template helper forms file into temporary place
- `makejconf` - Make jailv2 config file
- `makeresolv` - Manage jail /etc/resolv.conf file
- `makescene` - Make jail by scenario file
- `media` - [sys] Operate with virtual storage media such as ISO
- `merge` - Merge two ascii files with param into one
- `mkdatadir` - Mkdir in datadir for j2prepare and remove jail sysdata
- `mkdistribution` - [sys] Create default FreeBSD distribution in .txz files
- `mkinventory` - Collect and store inventory information
- `mkjhosts` - [sys] Simple manage records in hosts file
- `module` - Work with cbsd modules
- `mountfstab` - Mount jail by fstab file
- `mountmd` - Mount image file via md vnode to mroot

### N
- `natcfg` - Configure CBSD NAT service for RFC1918 Networks
- `natcfg-tui` - Configuring NAT in text-user dialog
- `natoff` - Disable NAT service for cbsd_nat_networks
- `naton` - Enable NAT service for RFC1918 Networks
- `ndescr` - [node] Show or modify node description
- `netinv` - Update Network-related information in inventory tables
- `nexttask` - [taskd] Execute first new task from taskd table
- `nics-list` - Return for visible storage
- `nlogin` - [node] Login to remote node and/or exec command
- `node` - [node] Manipulate or show information for remote nodes
- `nodeaddkey` - [node] Get rsa get from remote node
- `nodescp` - [node] get put file to remove nodes

### O-P
- `objls` - [build] List of object file
- `packages` - [sys] Create base-in-pkg packages/distribution
- `passwd` - [bsdconf] cbsd passwd wrapper
- `path2jail` - [jail] Make jail from specified root path
- `pkg` - [jail] Manage jail packages via pkg(7)
- `pkgbrowsecat` - Generate chosen package list from repository
- `pkgbrowser` - [jail] Generate chosen package list from repository
- `portsup` - Update FreeBSD ports tree in /usr/ports
- `preparebase` - [build] Misc fixes under base hier
- `pw` - [bsdconf] cbsd pw wrapper

### Q-R
- `qconstruct-tui` - [qemu] Ncurses based QEMU guest creation wizard
- `qexec` - [qemu] Execution for command inside cloud-based vm
- `qlogin` - [qemu] Exec login into jail
- `rctlcounters` - Collect RCTL count for jail if available
- `register_base` - [jail,sys] Register basedir for jails in CBSD CB
- `register_kernel` - [build] Register kernels for jails
- `register_source` - [build] Register sources for jails
- `removebase` - [build] Remove base dir
- `removekernel` - [build] Remove base dir
- `removeobj` - Remove obj-dir
- `removesrc` - Remove src-dir
- `replacewdir` - Replace for workdir
- `repo` - Working with CBSD Repository
- `repo-tui` - Ncurses based repo interface
- `retrinv` - Fetch sqldb from remote node
- `rexe` - [sys] Execute remote command using SSH
- `rsyncdoff` - Disable RSYNC service for jail migration
- `rsyncdon` - Enable RSYNC service for jail migration

### S
- `secretsfile` - Generate secrets file for jail
- `service` - [jail,sys] CBSD service wrapper
- `show_profile_list` - [bhyve,qemu,xen] Scan/print VM profiles
- `sockstat` - [jail] return list open sockets for jail
- `sources` - [sys] Show BSD sources
- `sqlrep` - [taskd] Execute first new task from taskd table
- `srcpatch` - Apply CBSD patch for FreeBSD source tree
- `srcup` - Update base source tree in ~cbsd/src directory
- `srvbrowser-tui` - [jail,sys] TUI to build/select services
- `ssh` - [bsdconf] OpenSSH jail helper
- `sshkey` - Manage node ssh key
- `summary` - [sys] Show summary info/statistics
- `sysinv` - Collect system-related information
- `sysrc` - [jail] CBSD sysrc wrapper

### T-U
- `task` - [taskd] Task queue management
- `taskls` - [taskd] List of task queue and status
- `trafstat` - Show traffic statistics for virtual environment
- `tzsetup` - [bsdconf] cbsd tzsetup wrapper
- `unmountfstab` - Unmount jail by fstab file
- `unmountmd` - unmount image file from jroot
- `unregister_base` - [jail,sys] Unregister bases from CBSD DB
- `unregister_kernel` - [build] Unregister kernel from databases
- `up` - [bhyve,jail,qemu] create env from CBSDfile
- `upgrade` - Upgrade base and/or kernel from other prepared hier
- `userlist` - Show user list

### V-Z
- `valecfg` - [bhyve] Operate with virtual VALE switch
- `valecfg-tui` - [bhyve] VALE switch TUI
- `vconfig` - [virtualbox] Configure for Virtualbox
- `vconstruct-tui` - [virtualbox] VirtualBox guest creation wizard
- `vcontrol-tui` - [virtualbox] Control for VBOX
- `vcreate` - [virtualbox] Create VirtualBox from config
- `vhidcfg` - [bhyve] Operate with bhyve disk images
- `vls` - [virtualbox] List virtualbox VM and status
- `vm-cpu-topology` - [sys] Operate with CPU topology
- `vm-packages` - [bhyve,jail,qemu,xen] Operate with vm_packages
- `vpc` - [sys] Operate with CBSD VPC
- `vremove` - [bhyve] Destroy VBOX domain
- `vset` - [virtualbox] Modify parameter for jail
- `vstart` - [virtualbox] Start virtualbox
- `vstop` - [virtualbox] Stop virtualbox
- `xcheckpoint` - [xen] xen checkpoint
- `xconfig` - [xen] Configure XEN domain
- `xconstruct-tui` - [xen] Xen guest creation wizard
- `xen-dsk` - [xen] Manage XEN disks
- `xls` - [xen] List XEN domain and status
- `xstart` - [xen] Start XEN domain
- `xstop` - [xen] Stop XEN domain
- `zfs-migrator` - [sys] ZFS migrator for CBSD
- `zfsinstall` - [helpers] mfsBSD ZFS install script

### Notes on Command Categories
- [bhyve] - Bhyve virtualization commands
- [jail] - FreeBSD jail management
- [sys] - System-level operations
- [build] - Source building utilities
- [bsdconf] - BSD configuration helpers
- [taskd] - Task daemon operations

### Command Format
All commands follow the format:
```sh
cbsd <command> [options]
```

For detailed help on any command:
```sh
cbsd help <command>
``` 