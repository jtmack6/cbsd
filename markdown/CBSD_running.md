# CBSD Directory Structure

This document details the directory structure of a running CBSD installation.

## Core Directories

### System Configuration
- `.rssh/` - Remote SSH configuration and keys
- `.ssh/` - SSH configuration and keys
- `etc/` - CBSD configuration files
- `rc.conf` - Main CBSD configuration
- `ver` - CBSD version information
- `nodename` - Current node name

### Node Management
- `nodes/` - Remote node configurations
- `node.domain` - Node domain information
- `node.location` - Node location metadata
- `node.role` - Node role definition
- `node.descr` - Node description
- `node.notes` - Node-specific notes
- `nc.inventory` - Node capability inventory

### Jail Management
- `jails/` - Active jail containers
- `jails-data/` - Jail data directories
- `jails-fstab/` - Jail fstab configurations
- `jails-rcconf/` - Jail rc.conf files
- `jails-system/` - Jail system files
- `basejail/` - Base jail templates

### Virtual Machine Management
- `vm/` - Virtual machine configurations and data

### Storage
- `src/` - Source files
- `tmp/` - Temporary files
- `ftmp/` - Formfile temporary storage
- `var/` - Variable data

### Import/Export
- `import/` - Import directory for environments
- `export/` - Export directory for environments

### Forms and Modules
- `formfile/` - Form configurations
- `modules/` - CBSD modules
- `cmd.subr` - Command subroutines
- `share/` - Shared resources

## Key Components

### Jail Management
```plaintext
jails/
├── <jailname>          # Individual jail directory
jails-data/
├── <jailname>-data     # Jail-specific data
jails-fstab/
├── fstab.<jailname>    # Jail filesystem configuration
jails-rcconf/
├── rc.conf_<jailname>  # Jail rc.conf settings
```

### VM Management
```plaintext
vm/
├── <vmname>            # VM configuration directory
├── <vmname>.img        # VM disk images
└── iso/                # ISO storage
```

### Node Configuration
```plaintext
nodes/
├── <nodename>/         # Remote node configuration
└── inventories/        # Node capabilities
```

## Important Files

### System Configuration
- `rc.conf`: Main CBSD configuration file
- `nodename`: Contains the node's hostname
- `node.domain`: Node's domain name
- `ver`: CBSD version information

### Node Information
- `node.descr`: Description of the node
- `node.notes`: Administrative notes
- `node.role`: Node's role in cluster
- `node.location`: Physical/logical location

## Usage Notes

1. **Data Persistence**:
   - `jails-data/` contains persistent jail data
   - `vm/` holds VM disk images and configurations
   - `export/` is used for environment backups

2. **Configuration Hierarchy**:
   - System-wide settings in `rc.conf`
   - Jail-specific settings in `jails-rcconf/`
   - VM-specific settings in `vm/`

3. **Security**:
   - SSH keys in `.ssh/` and `.rssh/` should be properly secured
   - Sensitive data should not be stored in `tmp/` or `ftmp/`

4. **Maintenance**:
   - Regular backups of `jails-data/` and `vm/` recommended
   - Clean `tmp/` and `ftmp/` periodically
   - Monitor `var/` for logs and status information

## Best Practices

1. **Organization**:
   - Keep jail data organized in `jails-data/`
   - Maintain clean import/export directories
   - Document node information in node.* files

2. **Backup Strategy**:
   - Regular backups of critical directories
   - Export important environments
   - Version control for configurations

3. **Security**:
   - Regular key rotation in `.ssh/`
   - Proper permissions on sensitive directories
   - Monitoring of system logs

4. **Maintenance**:
   - Regular cleanup of temporary directories
   - Update base jails in `basejail/`
   - Keep node inventory current 