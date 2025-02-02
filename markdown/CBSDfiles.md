# CBSDfile Guide

CBSDfile is CBSD's equivalent to Docker's Dockerfile, allowing you to define and manage environments declaratively. It supports both jails and bhyve virtual machines.

## CBSDfile Format

A CBSDfile is a shell script that describes one or more CBSD environments using shell functions.

### Basic Structure

```sh
# Basic CBSDfile example
quiet=0

jail_test1()
{
    ip4_addr="DHCP"
    host_hostname="${jname}.my.domain"
    mount_devfs=1
    allow_mount=1
    allow_devfs=1
    allow_nullfs=1
    mount_fstab=1
    astart=1
    interface="auto"
    
    # Package list for pkg install
    pkglist="nginx php80 mysql80-server"
}

bhyve_test1()
{
    vm_cpus="1"
    vm_ram="1g"
    vm_os_type="freebsd"
    vm_os_profile="FreeBSD-13.2-RELEASE-amd64"
    vm_hostbridge="amd"
    bhyve_flags="1"
    cd_boot_firmware="bhyve"
    ip4_addr="DHCP"
}

# Optional pre-start hook
preup_test1()
{
    # Commands to run before starting the environment
    echo "Preparing environment..."
}

# Optional post-start hook
postup_test1()
{
    # Commands to run after starting the environment
    echo "Environment is ready"
}
```

### Common Parameters

#### Jail Parameters
- `ip4_addr`: IP address (can be DHCP or static)
- `host_hostname`: Hostname for the jail
- `mount_devfs`: Enable devfs mounting
- `allow_mount`: Allow mounting filesystems
- `pkglist`: Space-separated list of packages to install

#### Bhyve Parameters
- `vm_cpus`: Number of virtual CPUs
- `vm_ram`: RAM allocation
- `vm_os_type`: Operating system type
- `vm_os_profile`: OS installation profile
- `ip4_addr`: IP address configuration

## CBSD Up/Down Commands

### cbsd up

The `up` command creates and starts environments defined in a CBSDfile.

```bash
cbsd up
```

Options:
- `-f <file>`: Specify alternative CBSDfile path
- `-j <jail>`: Start specific environment only
- `-r`: Remove before creating (recreate)

### cbsd down

The `down` command stops and optionally removes environments defined in a CBSDfile.

```bash
cbsd down
```

Options:
- `-f <file>`: Specify alternative CBSDfile path
- `-j <jail>`: Stop specific environment only
- `-r`: Remove after stopping

## Working with CBSDfiles

### Example Workflow

1. Create a CBSDfile in your project directory
2. Define your environments using shell functions
3. Start environments:
   ```bash
   cbsd up
   ```
4. Stop environments:
   ```bash
   cbsd down
   ```

### Multiple Environments

You can define multiple environments in a single CBSDfile by creating separate functions for each environment. The function name should be in the format:
- `jail_<name>()` for jails
- `bhyve_<name>()` for bhyve VMs
- `preup_<name>()` for pre-start hooks
- `postup_<name>()` for post-start hooks

### Environment Variables

CBSDfiles support environment variable usage:

```sh
jail_test1()
{
    host_hostname="${HOSTNAME:-default.hostname}"
    ip4_addr="${IP_ADDR:-DHCP}"
}
```

## Best Practices

1. Version control your CBSDfiles
2. Use environment variables for configuration that changes between deployments
3. Keep related services in the same CBSDfile
4. Document any special requirements or dependencies
5. Use meaningful names for your environments

## Notes

- CBSDfiles must be in the current working directory by default
- Environment names must be unique across your CBSD installation
- Always verify your CBSDfile syntax before deployment
- Consider using `cbsd up -r` during development to ensure clean state
