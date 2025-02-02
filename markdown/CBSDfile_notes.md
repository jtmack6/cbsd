# CBSDfile Configuration Options

This document details the various configuration options available in CBSDfiles for different environment types.

## Bhyve VM Options

### Basic VM Configuration
```sh
bhyve_vmname()
{
    # VM Resources
    vm_cpus="1"                         # Number of virtual CPUs
    vm_ram="1g"                         # RAM allocation (supports g/m suffixes)
    vm_cpu_topology="1/1/1"             # CPU topology (threads/cores/sockets)
    imgsize="10g"                       # Disk image size
    vm_iso_path="/path/to/iso"          # Installation ISO path

    # VM Type and Profile
    vm_os_type="freebsd"                # OS type (freebsd, linux, windows)
    vm_os_profile="FreeBSD-13.2"        # OS installation profile
    vm_hostbridge="amd"                 # Host bridge type (amd/intel)
    bhyve_flags="1"                     # Enable bhyve features
    cd_boot_firmware="bhyve"            # Boot firmware type
    hdd_boot_firmware="bhyve"           # HDD boot firmware

    # Networking
    ip4_addr="DHCP"                     # IP address (DHCP or static)
    vm_netif="virtio-net"               # Network interface type
    netif="bridge1"                     # Bridge interface
    interface="auto"                     # Auto-select interface

    # Storage Configuration
    virtio_type="virtio-blk"            # Disk controller type
    zfs_snapsrc=""                      # ZFS snapshot source
    zfs_encryption="0"                   # ZFS encryption

    # Display and Console
    vm_vnc_port="0"                     # VNC port (0=auto)
    vm_efi="1"                          # Enable EFI boot
    vm_console="nmdm"                   # Console type
    vm_rts="1"                          # Enable tablet support

    # Runtime Behavior
    astart="1"                          # Auto-start with node
    protected="0"                       # Protection from removal
    hidden="0"                          # Hide from list
}
```

### Advanced Features

#### CPU Features
```sh
bhyve_vmname()
{
    # CPU Feature Control
    vm_cpu_mode="custom"                # CPU mode (host-passthrough, custom)
    vm_cpu_flags="sse4.1,aes"          # Enabled CPU flags
    vm_cpu_mask="0-1"                   # CPU affinity mask
    vm_cpu_limit="50%"                  # CPU usage limit
}
```

#### Storage Options
```sh
bhyve_vmname()
{
    # Multiple Disks
    additional_hdd="1"                  # Enable additional disks
    dsk_controller="virtio-blk"         # Disk controller type
    dsk_size0="10g"                     # Size of first additional disk
    dsk_size1="20g"                     # Size of second additional disk
    dsk_type="zvol"                     # Disk backend type
    dsk_zfs_options=""                  # ZFS options for disks
}
```

#### Network Configuration
```sh
bhyve_vmname()
{
    # Multiple NICs
    nic_hwaddr="auto"                   # MAC address
    nic_parent="bridge1"                # Parent interface
    nic_persistent="1"                  # Persistent MAC
    vm_port_tcp="22,80,443"            # Forward TCP ports
    vm_port_udp="53"                    # Forward UDP ports
}
```

#### Resource Controls
```sh
bhyve_vmname()
{
    # Resource Limits
    vm_ram_max="4g"                     # Maximum RAM allocation
    vm_cpus_max="4"                     # Maximum CPU allocation
    vm_nice="1"                         # Nice value
    vm_ionice="3"                       # IO priority
}
```

### Hooks and Customization

#### Pre-start Configuration
```sh
preup_vmname()
{
    # Pre-start checks and setup
    local _required_packages="bhyve-fw bhyve-grub"
    
    # Check for required packages
    for _pkg in ${_required_packages}; do
        if ! pkg info -e ${_pkg}; then
            err 1 "${N1_COLOR}preup failed: required package not installed: ${N2_COLOR}${_pkg}${N0_COLOR}"
        fi
    done
}
```

#### Post-start Configuration
```sh
postup_vmname()
{
    # Post-start configuration
    # Wait for VM to be ready
    sleep 5
    
    # Configure networking
    jexec ${jname} sysrc hostname="${host_hostname}"
}
```

### User Management

#### Linux VM User Configuration
```sh
bhyve_vmname()
{
    # Basic VM settings as before...

    # User Configuration
    user_add="cbsd"                     # Username to create
    user_home="/home/cbsd"              # Home directory
    user_shell="/bin/bash"              # Default shell
    user_gecos="CBSD User"             # GECOS field
    user_uid="1001"                    # User ID (optional)
    user_gid="1001"                    # Group ID (optional)
    
    # SSH Key Configuration
    user_pubkey="ssh-rsa AAAA... user@host"    # SSH public key
    user_pw_user="cbsd"                # Username for password
    user_pw_root="rootpass"            # Root password (if needed)
    
    # Sudo Configuration
    user_pw_wheel="0"                  # Add to wheel group
    user_pw_sudo="1"                   # Enable sudo access
}

# Optional post-creation user setup
postup_vmname()
{
    # Wait for VM to be ready
    sleep 5
    
    # Additional user configuration if needed
    # Example: Add additional groups or permissions
    jexec ${jname} pw groupadd -n docker
    jexec ${jname} pw groupmod docker -m ${user_add}
}
```

#### Important Notes for User Management

- The `user_add` parameter creates the primary user account
- SSH keys should be properly formatted and include the full public key
- For secure deployments, avoid storing passwords in CBSDfiles
- Use environment variables for sensitive data:
  ```sh
  user_pubkey="${SSH_PUBLIC_KEY}"
  user_pw_root="${ROOT_PASSWORD}"
  ```
- The `user_pw_wheel` and `user_pw_sudo` options control administrative access
- Post-creation setup can be done via the `postup` hook

## Notes

- Not all options are required; CBSD will use defaults for unspecified values
- Some options are interdependent (e.g., vm_efi and cd_boot_firmware)
- Resource limits should be set according to host capabilities
- Network configuration depends on host network setup
- Storage options depend on available storage backends

## Best Practices

1. Always specify resource limits to prevent resource exhaustion
2. Use meaningful names for VMs and their components
3. Document custom configurations
4. Test configurations in development before production
5. Use hooks for complex setup requirements 