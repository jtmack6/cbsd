# CBSD etc Directory Structure

The `/etc` directory in CBSD contains configuration files that define system behavior, defaults, and templates.

## Core Configuration Files

- `Makefile` - Build instructions for CBSD configuration
- `cbsd.mtree` - Directory hierarchy specification
- `cbsd_sudoers` - SUDO configuration for CBSD operations
- `modules.conf` - Module configuration and loading
- `pf.conf` - Base PF firewall configuration
- `pfcustomflt.conf` - Custom PF filters
- `pfnat.conf` - NAT rules for PF
- `pfrdr.conf` - Port forwarding rules
- `rsyncd.conf` - RSYNC daemon configuration
- `spice.conf` - SPICE remote display configuration

## Defaults Directory (`defaults/`)

### Operating System Configurations

#### FreeBSD
- `FreeBSD-bases.conf` - Base system configurations
- `FreeBSD-baseupdate.conf` - Base update settings
- `FreeBSD-kernels.conf` - Kernel configurations
- `FreeBSD-sources.conf` - Source code settings
- `FreeBSD-userlist.conf` - User management defaults

#### Other BSDs
- `DragonFly-bases.conf` - DragonFlyBSD base settings
- `HardenedBSD-bases.conf` - HardenedBSD base settings
- `Linux-bases.conf` - Linux compatibility settings

### Kernel Configurations
- `FreeBSD-kernel-BHYVE-*` - Bhyve-optimized kernel configs
- `FreeBSD-kernel-CBSD-*` - CBSD-specific kernel configs
- `FreeBSD-kernel-GENERIC-*` - Standard kernel configs
- `FreeBSD-kernel-FIRE-*` - Firewall-focused configs

### Virtual Machine Templates

#### Standard Operating System Profiles

| OS Family | Distribution | Version | Profile | Notes |
|-----------|-------------|----------|---------|-------|
| FreeBSD | FreeBSD | 13.2 | `FreeBSD-x64-13.2` | Standard install |
| | | 13.3 | `FreeBSD-x64-13.3` | |
| | | 13.4 | `FreeBSD-x64-13.4` | |
| | | 14.1 | `FreeBSD-x64-14.1` | |
| | | 14.2 | `FreeBSD-x64-14.2` | |
| | | 15.0 | `FreeBSD-x64-15.0` | |
| | GhostBSD | 24 | `GhostBSD-x64-24` | Desktop focused |
| | OPNsense | 24 | `OPNsense-24-RELEASE-amd64` | Firewall |
| | | 22 | `OPNsense-22-RELEASE-amd64` | |
| | TrueNAS | 13 | `TrueNAS-CORE-x64-13` | Storage |
| Linux | Alpine | 3 | `Alpine-standart-3` | Minimal |
| | | 3 | `Alpine-extended-3` | Full featured |
| | Arch | 2024 | `ArchLinux-x86-2024` | Rolling release |
| | Fedora | 41 | `fedora-server-41-x86_64` | Server edition |
| | | 40 | `fedora-server-40-x86_64` | |
| | | 40 | `fedora-silverblue-40-x86_64` | Immutable desktop |
| | Mint | 22 | `Mint-22` | Desktop focused |
| | Ubuntu Desktop | 24.04 | `ubuntu-desktop-amd64-24` | LTS Desktop |
| | | 23.10 | `ubuntu-desktop-amd64-23` | Interim |
| | | 22.04 | `ubuntu-desktop-amd64-22` | LTS Desktop |
| | Kubuntu | 24.04 | `kubuntu-desktop-amd64-24` | KDE Desktop |
| | | 22.04 | `kubuntu-desktop-amd64-22` | |
| BSD | OpenBSD | 7.5 | `openbsd-x86-7` | Standard install |
| | | 7.0 | `openbsd-x86-7` | |
| | NetBSD | 10.1 | `netbsd-x86-10` | Standard install |
| | | 9.0 | `netbsd-x86-9` | |
| | DragonFlyBSD | 6.x | `dflybsd-x86-6` | HAMMER filesystem |
| Windows | Windows 11 | 22H2 | `11_86x_64x` | x64 only |
| | Windows 10 | 22H2 | `10_86x_64x` | x86/x64 |
| | Windows 7 | SP1 | `7_86x_64x` | Legacy |
| Other | ReactOS | Latest | `ReactOS` | Windows alternative |
| | Haiku | r1 | `Haiku-r1` | BeOS inspired |
| | FreeDOS | Latest | `FreeDOS` | DOS compatible |

#### Cloud-Init Enabled Profiles

| OS Family | Distribution | Version | Profile | Notes |
|-----------|-------------|----------|---------|-------|
| FreeBSD | FreeBSD UFS | 13.2 | `cloud-FreeBSD-ufs-x64-13.2` | UFS filesystem |
| | | 13.3 | `cloud-FreeBSD-ufs-x64-13.3` | |
| | | 13.4 | `cloud-FreeBSD-ufs-x64-13.4` | |
| | | 14.1 | `cloud-FreeBSD-ufs-x64-14.1` | |
| | | 14.2 | `cloud-FreeBSD-ufs-x64-14.2` | |
| | | 15.0 | `cloud-FreeBSD-ufs-x64-15.0` | |
| | FreeBSD ZFS | 13.2 | `cloud-FreeBSD-zfs-x64-13.2` | ZFS filesystem |
| | | 13.3 | `cloud-FreeBSD-zfs-x64-13.3` | |
| | | 13.4 | `cloud-FreeBSD-zfs-x64-13.4` | |
| | | 14.1 | `cloud-FreeBSD-zfs-x64-14.1` | |
| | | 14.2 | `cloud-FreeBSD-zfs-x64-14.2` | |
| | | 15.0 | `cloud-FreeBSD-zfs-x64-15.0` | |
| Linux | Debian | 12 | `cloud-Debian-x86-12` | Bookworm |
| | | 11 | `cloud-Debian-x86-11` | Bullseye |
| | | 9 | `cloud-Debian-x86-9` | Stretch |
| | Ubuntu Server | 24.04 | `cloud-ubuntuserver-amd64-24.04` | Noble (LTS) |
| | | 23.10 | `cloud-ubuntuserver-amd64-23.10` | Mantic |
| | | 23.04 | `cloud-ubuntuserver-amd64-23.04` | Lunar |
| | | 22.04 | `cloud-ubuntuserver-amd64-22.04` | Jammy (LTS) |
| | | 20.04 | `cloud-ubuntuserver-amd64-20.04` | Focal (LTS) |
| | Rocky | 9 | `cloud-Rocky-9-x86_64` | Enterprise Linux |
| | | 8 | `cloud-Rocky-8-x86_64` | |
| | AlmaLinux | 9 | `cloud-Alma-9-x86_64` | Enterprise Linux |
| | Oracle | 9 | `cloud-Oracle-9-x86_64` | Enterprise Linux |
| | | 8 | `cloud-Oracle-8-x86_64` | |
| | | 7 | `cloud-Oracle-7-x86_64` | |
| | Fedora | 41 | `cloud-Fedora-41-x86_64` | Latest release |
| | | 40 | `cloud-Fedora-40-x86_64` | |
| | | 39 | `cloud-Fedora-39-x86_64` | |
| | Devuan | 5 | `cloud-Devuan-x86-5` | Systemd-free |
| | Kali | 2024 | `cloud-Kali-2024-amd64` | Security focused |
| BSD | NetBSD | 10.0 | `cloud-netbsd-x86-10.0` | Cloud ready |
| | | 9.0 | `cloud-netbsd-x86-9` | |

Notes:
- Cloud-init profiles support automated provisioning via cloud-init
- Version numbers match upstream release versions
- Architecture support:
  - amd64/x86_64: All listed distributions
  - arm64/aarch64: FreeBSD, Debian, Ubuntu
  - riscv64: FreeBSD only
- Filesystem variants:
  - FreeBSD supports both UFS and ZFS cloud images
  - Linux distributions use their default filesystem
- Release types:
  - LTS: Long Term Support (e.g., Ubuntu 22.04, 24.04)
  - Rolling: Continuous updates (Arch, Void)
  - Enterprise: Stable, long-support (Rocky, AlmaLinux)
- Desktop environments available for:
  - Ubuntu: GNOME, KDE, LXDE, Xfce
  - FreeBSD: Various window managers
  - Other: Distribution specific

#### FreeBSD VMs
- `vm-freebsd-FreeBSD-*.conf` - FreeBSD VM templates
- `vm-freebsd-cloud-*.conf` - Cloud-init enabled FreeBSD
- `vm-freebsd-GhostBSD-*.conf` - GhostBSD derivatives
- `vm-freebsd-OPNsense-*.conf` - OPNsense firewall

#### Linux VMs
- `vm-linux-*.conf` - Various Linux distribution templates
- `vm-linux-cloud-*.conf` - Cloud-init enabled Linux

#### Other OS VMs
- `vm-other-*.conf` - Other operating systems
- `vm-windows-*.conf` - Windows VM configurations

### Jail Templates
- `jail-freebsd-*.conf` - FreeBSD jail configurations
- `jail-freebsd-vnet.conf` - Network-isolated jail config

### Command Configurations
- `bstart.conf` - Bhyve start settings
- `bstop.conf` - Bhyve stop settings
- `jstart.conf` - Jail start settings
- `jstop.conf` - Jail stop settings

### Service Configurations
- `dhcpd.conf` - DHCP server settings
- `rsyncd.conf` - File sync settings
- `cbsdrsyncd.conf` - CBSD-specific rsync
- `cloud-init.conf` - Cloud initialization

### Resource Control
- `racct-*-statsd.conf` - Resource accounting
- `rctl-defaults.conf` - Resource control defaults
- `rctl-litejail.conf` - Lightweight jail limits

### Network Configuration
- `pf.conf.tpl` - PF firewall template
- `cbsd-pf.conf` - CBSD-specific firewall rules

### Build and Update
- `buildworld.conf` - World build settings
- `srcup.conf` - Source update configuration
- `upgrade.conf` - System upgrade settings

## Usage Notes

1. **Template Hierarchy**:
   - Base configurations in root `/etc`
   - Specific configurations in `/etc/defaults`
   - Custom configurations should override defaults

2. **Version Management**:
   - Multiple versions of OS configs maintained
   - Architecture-specific configurations available
   - Cloud and standard variants for VMs

3. **Security**:
   - PF firewall configurations
   - Resource control settings
   - Sudo permissions management

4. **Customization**:
   - Templates can be copied and modified
   - Default settings can be overridden
   - Multiple profile options available 