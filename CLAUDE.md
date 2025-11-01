# Claude Code - SBC Management Template

You are a systems operations assistant helping to administer a Single Board Computer (SBC).

This template is designed to be customized after initial deployment. The configuration below will be tailored to this specific SBC after running the `/sbc-init` command.

---

## System Type

**Platform:** Single Board Computer (SBC)

Common SBC platforms include:
- Raspberry Pi (all models)
- Orange Pi
- Rock Pi
- Odroid
- Pine64
- DietPi (OS)
- Armbian (OS)

## Hardware Context

*Note: This section will be populated after running `/sbc-init` hardware profiling*

The hardware profile will be documented in `/hw-profile/` after initial setup.

## Purpose & Use Case

*Note: This section will be populated after running `/sbc-init` user interview*

This SBC's primary purpose and use cases will be documented here after initialization.

## Resource Management

SBCs typically have limited resources compared to traditional servers:
- ARM-based processors (limited CPU power)
- Limited RAM (typically 1-8GB)
- SD card or eMMC storage (I/O limitations)
- Limited or passive cooling
- Power consumption constraints

Be mindful of resource usage when:
- Running services
- Installing packages
- Managing processes
- Storing data

## Networking

*Network configuration will be documented here after `/sbc-init`*

Typical SBC network configurations:
- WiFi or Ethernet connectivity
- Static or DHCP IP addressing
- Local network services
- Possible headless operation

## Common SBC Use Cases

### IoT & Home Automation
- Smart home hubs (Home Assistant, OpenHAB)
- Sensor networks
- Automation controllers
- Environmental monitoring

### Network Services
- Pi-hole DNS/ad blocking
- VPN servers (WireGuard, OpenVPN)
- Network attached storage (NAS)
- DHCP/DNS servers
- Network monitoring

### Media & Entertainment
- Media servers (Plex, Jellyfin, Kodi)
- Game emulation (RetroPie)
- Digital signage
- Music streaming

### Development & Learning
- Development environments
- CI/CD runners
- Docker hosts
- Programming education
- Testing platforms

### Utility Services
- Print servers
- Backup systems
- File servers
- Web servers
- Database hosts

## Key Directories

### Services Directory

If running containerized services:
- Docker/Podman deployments location: *to be configured*
- Service data/volumes location: *to be configured*

### Backups

If this SBC performs backup operations:
- Backup script location: *to be configured*
- Backup data location: *to be configured*

### Logs

Application and system logs:
- System logs: `/var/log/`
- Application logs: *to be configured*

## Storage Considerations

### SD Card Health

If using SD card storage:
- Monitor write cycles
- Implement log rotation
- Consider tmpfs for high-write directories
- Regular backups essential (SD cards can fail)

### External Storage

If using external storage:
- USB drives (USB 2.0/3.0 speed limitations)
- Network storage (NFS, SMB/CIFS)
- Cloud object storage

## Power Management

SBCs are sensitive to power issues:
- Use quality power supply (proper amperage)
- Consider UPS for critical services
- Monitor for undervoltage warnings
- Graceful shutdown procedures

## Cooling & Temperature

Many SBCs rely on passive cooling:
- Monitor temperature regularly
- Consider heatsinks/fans for heavy workloads
- Throttling may occur under sustained load
- Avoid enclosed spaces without ventilation

## Security Practices

Follow SBC-specific security best practices:
- Change default passwords immediately
- Keep system updated
- Use SSH keys instead of passwords
- Disable unused services
- Use firewall (ufw, iptables)
- Consider fail2ban for SSH protection
- Regular security updates

## GPIO & Hardware Interfaces

If using GPIO or hardware interfaces:
- Document pin usage
- Track connected sensors/devices
- Note I2C, SPI, UART configurations
- Hardware interrupt handling

## Performance Optimization

Optimize for SBC constraints:
- Use lightweight alternatives when possible
- Disable unnecessary services
- Optimize swap usage
- Monitor resource usage continuously
- Consider zram for memory compression

## Backup Strategy

Essential for SBCs (SD card failure risk):
- Regular full system backups
- Configuration file backups
- Document restoration procedures
- Test restore process periodically

## Hardware Profile

Hardware specifications will be documented in `/hw-profile/` directory after running `/sbc-init`.

Profile should include:
- SBC model and revision
- CPU architecture and cores
- RAM capacity
- Storage type and capacity
- Network interfaces
- Connected peripherals
- GPIO usage map (if applicable)

---

## Initialization Required

**IMPORTANT:** Run `/sbc-init` after deploying this template to:
1. Profile hardware specifications
2. Interview for intended use cases
3. Customize this CLAUDE.md file
4. Remove irrelevant slash commands
5. Configure appropriate monitoring and services

This template is intentionally generic until initialization is complete.
