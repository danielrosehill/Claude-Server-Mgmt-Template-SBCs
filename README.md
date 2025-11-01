# Claude Code - SBC Management Template

[![Claude Code](https://img.shields.io/badge/Claude%20Code-Project-8A2BE2?style=flat&logo=anthropic)](https://github.com/anthropics/claude-code)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A comprehensive Claude Code template for managing Single Board Computers (SBCs) like Raspberry Pi, Orange Pi, DietPi, and similar platforms.

## What This Template Provides

This repository offers a ready-to-deploy Claude Code environment specifically designed for SBC administration, including:

- **Smart initialization wizard** (`/sbc-init`) - Automatically profiles hardware and customizes configuration
- **Pre-configured CLAUDE.md** - SBC-specific context and best practices
- **38 slash commands** - System administration and monitoring commands
- **10 specialized agents** - Complex task automation
- **Hardware profiling** - Automatic detection and documentation
- **Resource-aware operations** - Optimized for constrained SBC hardware

---

## Quick Start

### 1. Clone the Template

On your SBC:

```bash
# Clone to your preferred location
cd ~
git clone https://github.com/yourusername/Claude-Code-SBC-Template.git
cd Claude-Code-SBC-Template
```

### 2. Deploy Configuration

Choose your deployment method:

```bash
# Option A: Deploy to home directory only (recommended)
./sync-to-home.sh

# Option B: Deploy system-wide (requires sudo)
./sync-to-home-and-root.sh
```

### 3. Initialize for Your SBC

Start Claude Code and run the initialization:

```bash
claude
```

Then in Claude Code:
```
/sbc-init
```

The initialization wizard will:
- ✅ Automatically profile your SBC hardware
- ✅ Interview you about your use cases
- ✅ Customize CLAUDE.md for your setup
- ✅ Remove irrelevant slash commands
- ✅ Configure appropriate monitoring
- ✅ Create helpful documentation

**That's it!** Your SBC management environment is ready.

---

## What Gets Customized

### Before `/sbc-init`
The template contains generic SBC guidance and all available commands.

### After `/sbc-init`
- **CLAUDE.md** is tailored with your actual hardware specs, network config, and use cases
- **Hardware profile** documents exact SBC model, CPU, RAM, storage, sensors
- **Slash commands** are pruned to only relevant ones for your setup
- **Monitoring** is configured for your specific constraints
- **Documentation** captures your network topology and services

---

## Supported Platforms

This template works with any ARM or x86-based SBC running Linux:

### Tested Platforms
- **Raspberry Pi** (all models: Zero, 3, 4, 5)
- **Orange Pi** (various models)
- **Rock Pi**
- **Odroid**
- **Pine64**

### Compatible Operating Systems
- Raspberry Pi OS (formerly Raspbian)
- DietPi
- Armbian
- Ubuntu for ARM
- Debian-based distributions

---

## What's Included

### Slash Commands (38 total)

Commands are organized by category and will be filtered based on your setup during `/sbc-init`.

#### Essential SBC Commands
- `/system-health` - Disk, memory, CPU, temperature monitoring
- `/resource-alerts` - Critical for resource-constrained SBCs
- `/process-monitor` - Identify resource hogs
- `/uptime-stats` - System stability metrics

#### Storage & Filesystem
- `/disk-usage` - Analyze space consumption (critical for SD cards)
- `/filesystem-health` - Check filesystem integrity
- `/cleanup-filesystem` - Free up space safely

#### Networking
- `/network-health` - Network configuration and connectivity
- `/check-lan-connectivity` - Verify local network access
- `/port-check` - Analyze listening services

#### Service Management
- `/check-services` - systemd service status
- `/docker-health` - Docker environment health (if using Docker)
- `/deployment-list` - Analyze all deployments

#### Security
- `/security-audit` - Comprehensive security check
- `/firewall-check` - Firewall configuration review
- `/certificate-check` - SSL/TLS certificate status

#### Monitoring & Logs
- `/analyze-logs` - System and service log examination
- `/boot-time` - Boot performance analysis
- `/check-logs-noteworthy` - General log review

#### Hardware Specific
- `/gpu-status` - GPU status (if applicable)
- `/benchmark-hardware` - Performance benchmarking
- `/document-distro` - Distribution documentation

### Specialized Agents (10 total)

Agents handle complex multi-step tasks:

- **docker-troubleshooter** - Docker issue diagnosis
- **backup-manager** - Backup operations and troubleshooting
- **log-analyzer** - Pattern detection in logs
- **service-monitor** - Service management and troubleshooting
- **security-auditor** - Vulnerability identification
- **performance-optimizer** - Resource optimization for SBCs
- **deployment-manager** - Manage containerized services
- **storage-manager** - Storage and filesystem management
- **server-documentarian** - Generate documentation
- **tunnel-manager** - Cloudflare Tunnel management (if used)

---

## Common SBC Use Cases

This template is optimized for typical SBC applications:

### Home Automation & IoT
- Home Assistant, OpenHAB
- Sensor networks and monitoring
- Smart home integration

### Network Services
- Pi-hole DNS ad blocking
- VPN servers (WireGuard, OpenVPN)
- Network monitoring (Prometheus, Grafana)
- DHCP/DNS servers

### Media & Entertainment
- Plex, Jellyfin, Kodi media servers
- Music streaming (Subsonic, Airsonic)
- Digital signage
- Game emulation (RetroPie)

### Development & DevOps
- CI/CD runners (Gitea, Jenkins)
- Docker host for microservices
- Testing environments
- Development platforms

### Utility Services
- File servers (Samba, NFS)
- Print servers (CUPS)
- Backup solutions
- Web hosting
- Database servers

---

## Directory Structure

```
Claude-Code-SBC-Template/
├── .claude/
│   ├── agents/          # Specialized task agents
│   └── commands/        # Slash commands
│       ├── sbc-init.md  # Initialization wizard ⭐
│       ├── general/     # General system commands
│       ├── docker/      # Container management
│       ├── networking/  # Network operations
│       └── ...
├── context/             # Generated configuration docs
├── hw-profile/          # Hardware profile data
├── CLAUDE.md           # Main AI assistant context
├── sync-to-home.sh     # Deploy to ~/
├── sync-to-home-and-root.sh  # Deploy system-wide
└── README.md           # This file
```

---

## Deployment Options Explained

### Option A: `sync-to-home.sh` (Recommended)

Deploys Claude Code configuration to your home directory:

```bash
./sync-to-home.sh
```

**Creates:**
- `~/CLAUDE.md` - Main configuration
- `~/.claude/` - Commands and agents
- `~/hw-profile/` - Symlink to repository

**Best for:**
- Single-user SBCs
- Personal projects
- Standard deployments

**No sudo required** ✅

### Option B: `sync-to-home-and-root.sh` (Advanced)

Deploys to both home directory AND filesystem root:

```bash
./sync-to-home-and-root.sh
```

**Creates:**
- Everything from Option A, plus:
- `/CLAUDE.md` - System-wide configuration
- `/.claude/` - System-level commands
- `/hw-profile/` - System-level symlink

**Best for:**
- Multi-user environments
- Running Claude Code with sudo
- System-level operations

**Requires sudo** ⚠️

---

## SBC-Specific Features

### Resource Awareness
- Monitors temperature to prevent throttling
- Tracks memory carefully on low-RAM systems
- SD card write minimization strategies
- Swap optimization recommendations

### Power Management
- Undervoltage detection (Raspberry Pi)
- Power consumption monitoring
- Graceful shutdown procedures
- Battery/solar power considerations

### Storage Optimization
- SD card health monitoring
- Log rotation configuration
- tmpfs for high-write directories
- External storage integration

### Cooling & Thermal Management
- Temperature monitoring and alerts
- Throttling detection
- Cooling solution recommendations
- Safe overclocking guidance (where applicable)

### GPIO & Hardware
- GPIO pin usage documentation
- I2C, SPI, UART interface tracking
- Sensor integration support
- HAT compatibility notes

---

## After Initialization

Once `/sbc-init` completes, you'll have:

### Generated Documentation
- **context/sbc-config.md** - Complete configuration
- **context/network-map.md** - Network topology
- **context/services-inventory.md** - Running services
- **hw-profile/sbc-specs.md** - Detailed hardware specs
- **hw-profile/temperature-baselines.md** - Normal temps
- **hw-profile/performance-baselines.md** - Performance metrics

### Helper Scripts
Created in `~/sbc-scripts/`:
- `temp-check.sh` - Quick temperature check
- `resource-status.sh` - System status at a glance
- `service-status.sh` - All services status
- `backup-trigger.sh` - Manual backup (if configured)

### Customized Commands
Only the slash commands relevant to your setup will be recommended for use.

---

## Updating Configuration

### Re-running Initialization
To reconfigure completely:
```bash
claude
/sbc-init
```

### Manual Updates
Edit files in the repository, then re-sync:
```bash
cd ~/Claude-Code-SBC-Template
# Edit CLAUDE.md or .claude/commands as needed
./sync-to-home.sh  # Redeploy changes
```

### Pulling Template Updates
```bash
cd ~/Claude-Code-SBC-Template
git pull origin main
./sync-to-home.sh  # Deploy updated files
```

---

## Security Considerations

This template follows SBC security best practices:

- ✅ Encourages SSH key authentication
- ✅ Recommends firewall configuration (ufw)
- ✅ Suggests fail2ban for SSH protection
- ✅ Promotes minimal service exposure
- ✅ Regular security updates
- ✅ Principle of least privilege

**Important:** Change default passwords immediately after deploying any SBC!

---

## Troubleshooting

### Commands Not Showing Up

Ensure you've run the sync script:
```bash
./sync-to-home.sh
```

Then restart Claude Code.

### Initialization Not Working

Make sure you're running the latest Claude Code CLI:
```bash
claude --version
```

### Hardware Detection Issues

Some SBC models may need additional packages:
```bash
sudo apt update
sudo apt install -y lshw dmidecode inxi
```

---

## Contributing

This is a template repository designed to be forked and customized. However, improvements to the base template are welcome:

1. Fork the repository
2. Create a feature branch
3. Make your improvements
4. Submit a pull request

**Focus areas for contributions:**
- Additional SBC platform support
- New slash commands for common SBC tasks
- Improved hardware detection
- Better resource optimization strategies

---

## License

This template is released under the MIT License. See LICENSE file for details.

You are free to:
- Use for personal or commercial projects
- Modify and customize
- Share and redistribute

---

## Related Projects

- [Claude Code](https://github.com/anthropics/claude-code) - Official Claude Code CLI
- [Claude Code Projects Index](https://github.com/danielrosehill/Claude-Code-Repos-Index) - Collection of Claude Code projects

---

## Support & Community

- **Issues:** Report bugs or request features via GitHub Issues
- **Discussions:** Share your SBC setups and ask questions in Discussions
- **Documentation:** Full Claude Code documentation at [docs.claude.com](https://docs.claude.com)

---

## Version History

### v1.0.0 - Initial SBC Template Release
- SBC-focused CLAUDE.md with generic hardware context
- `/sbc-init` automatic configuration wizard
- 38 slash commands adapted for SBC use
- 10 specialized agents for SBC administration
- Automatic hardware profiling
- Resource-aware monitoring and optimization

---

## Author

Created as a template for the Claude Code community.

**Based on:** Claude Server Manager Template
**Adapted for:** Single Board Computer management
**Optimized for:** Resource-constrained ARM-based systems

---

**Start managing your SBC with AI assistance today!**

Run `/sbc-init` after deployment and let Claude Code customize everything for your specific hardware and use case.
