# SBC Initialization & Configuration

Welcome! You've deployed the Claude Code SBC Management Template. This initialization process will:

1. **Profile your SBC hardware** - Automatically detect and document specifications
2. **Interview you about use cases** - Understand how you'll use this SBC
3. **Customize CLAUDE.md** - Tailor the configuration to your specific setup
4. **Optimize slash commands** - Remove irrelevant commands and keep useful ones
5. **Configure monitoring** - Set up appropriate resource monitoring for your hardware

Let's get started!

---

## Step 1: Hardware Profiling

First, let me gather detailed hardware information about this SBC.

**Actions to take:**
1. Detect SBC model and revision (check `/proc/cpuinfo`, `/proc/device-tree/model` if available)
2. Identify CPU architecture, cores, and frequency
3. Check RAM capacity and swap configuration
4. Identify storage type (SD card, eMMC, USB, SSD)
5. Check network interfaces (WiFi, Ethernet, their status)
6. Detect GPU/video capabilities if present
7. Check temperature sensors and cooling
8. Identify GPIO availability (if Raspberry Pi or similar)
9. Check for hardware accelerators (crypto, video encoding, etc.)

**Save all findings to:** `/hw-profile/sbc-specs.md`

Include in the profile:
- Exact SBC model and revision
- CPU: architecture, model, cores, current/max frequency
- Memory: total RAM, available, swap configuration
- Storage: device type, capacity, filesystem, mount points
- Network: interfaces, MAC addresses, current IP configuration
- Temperature: current readings and available sensors
- Power: any undervoltage or throttling indicators
- GPIO: available pins and current usage
- Special hardware: cameras, displays, HATs, connected sensors

---

## Step 2: User Interview

Now I need to understand how you plan to use this SBC. Please answer the following:

### Primary Purpose
**What is the main purpose of this SBC?**

Common categories:
- [ ] Home Automation / IoT Hub
- [ ] Network Services (DNS, VPN, monitoring)
- [ ] Media Server (Plex, Jellyfin, Kodi)
- [ ] Development/Testing Platform
- [ ] File/Print Server
- [ ] Backup System
- [ ] Learning/Education
- [ ] Gaming/Emulation
- [ ] Other (please specify)

### Specific Services

**What specific services or applications will run on this SBC?**

Examples:
- Pi-hole, AdGuard Home
- Home Assistant, OpenHAB
- Docker containers (which ones?)
- Web server (nginx, Apache)
- Database (PostgreSQL, MySQL, SQLite)
- VPN (WireGuard, OpenVPN)
- File sharing (Samba, NFS)
- Media services (Plex, Jellyfin)
- Monitoring tools
- Other applications

### Resource Constraints

**Are there any specific resource concerns?**
- Is the SBC running 24/7 or intermittently?
- Using SD card (need to minimize writes)?
- Limited cooling (need to monitor temperature closely)?
- Power constraints (battery powered, solar)?
- Network bandwidth limitations?

### Network Configuration

**Network setup details:**
- What's your home/local network range? (e.g., 192.168.1.0/24, 10.0.0.0/24)
- Gateway/router IP?
- This SBC's IP address (static or DHCP)?
- Any other important devices (NAS, other servers, IoT devices)?
- How will you access this SBC? (SSH only, web interface, VNC?)
- Do you need external access? (Cloudflare Tunnel, port forwarding, VPN?)

### Storage & Backups

**Storage configuration:**
- What storage are you using? (SD card size, external USB drive, network storage)
- Do you need backup functionality?
- Should this SBC back up to somewhere else (NAS, cloud)?
- Should backups of this SBC be made elsewhere?

### Security & Access

**Security preferences:**
- Firewall configuration needed? (ufw, iptables)
- fail2ban for SSH protection?
- Security monitoring requirements?
- Multi-user access or single admin?

### Monitoring Priorities

**What should be monitored most closely?**
- Temperature (prevent thermal throttling)
- Disk space (especially on small SD cards)
- Memory usage
- Network connectivity
- Service uptime
- Power/undervoltage warnings
- Specific application metrics

---

## Step 3: Automatic Configuration

Based on your answers, I will now:

### A. Update CLAUDE.md

Update the following sections in CLAUDE.md:
- **Hardware Context** - Write detailed specs from profiling
- **Purpose & Use Case** - Document your intended use
- **Networking** - Add your network configuration
- **Key Directories** - Specify actual directory paths
- **Resource Management** - Add specific constraints and monitoring needs
- **Storage Considerations** - Document storage type and backup strategy

### B. Optimize Slash Commands

Review the included slash commands and:

**Keep these essential commands:**
- `/system-health` - Always useful for SBCs
- `/resource-alerts` - Critical for constrained hardware
- `/check-services` - Important for service monitoring
- `/network-health` - Essential for network troubleshooting

**Conditionally keep based on your setup:**
- Docker commands (if using Docker)
- Backup commands (if doing backups)
- GPU commands (if GPU present and used)
- NFS/storage commands (if using network storage)
- Tunnel commands (if using Cloudflare Tunnel)

**Remove if not applicable:**
- Proxmox-related commands (if not running as VM)
- RAID commands (if single disk)
- High-end hardware commands (if not applicable)

### C. Configure Monitoring

Set up appropriate monitoring for SBC:
- Temperature monitoring script (critical for SBCs)
- Disk space alerts (important for SD cards)
- Service watchdogs for critical applications
- Undervoltage detection (for Raspberry Pi)
- Network connectivity checks

### D. Create Helper Scripts

Generate useful scripts in `~/sbc-scripts/`:
- `temp-check.sh` - Quick temperature check
- `resource-status.sh` - CPU, memory, disk at a glance
- `service-status.sh` - Check all configured services
- `backup-trigger.sh` - Manual backup trigger (if applicable)

---

## Step 4: Documentation

Create comprehensive documentation:

**In /context/:**
- `sbc-config.md` - Complete SBC configuration details
- `network-map.md` - Network topology and device info
- `services-inventory.md` - All running services and their purposes

**In /hw-profile/:**
- `sbc-specs.md` - Detailed hardware profile
- `temperature-baselines.md` - Normal operating temperatures
- `performance-baselines.md` - Baseline performance metrics

---

## Step 5: Recommendations

Based on the hardware profile and intended use, provide:

1. **Performance Recommendations**
   - Suggested memory split (if Raspberry Pi with GPU)
   - Swap configuration recommendations
   - Filesystem optimizations
   - Overclocking safety (if applicable)

2. **Security Hardening**
   - Firewall rules to implement
   - Services to disable
   - Update strategy

3. **Reliability Improvements**
   - Backup strategy recommendations
   - SD card longevity tips
   - Cooling solutions if needed
   - Power supply recommendations

4. **Additional Slash Commands to Consider**
   - Custom commands for your specific use case
   - Integration commands for your services

---

## Completion

After this initialization:

1. ✅ CLAUDE.md is customized for your SBC
2. ✅ Hardware profile is documented
3. ✅ Slash commands are optimized
4. ✅ Monitoring is configured
5. ✅ Helper scripts are created
6. ✅ Documentation is complete

**Next Steps:**
- Run `/system-health` to verify monitoring
- Check `/resource-alerts` to establish baselines
- Review the customized slash commands
- Test helper scripts in `~/sbc-scripts/`
- Set up any recommended services or configurations

**To update this configuration in the future**, you can:
- Re-run `/sbc-init` to reconfigure
- Manually edit CLAUDE.md as needs change
- Run the sync script to propagate changes

Your SBC management environment is now ready for use!
