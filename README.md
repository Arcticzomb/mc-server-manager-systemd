# Minecraft Server Systemd Manager

A systemd-based service manager for Minecraft servers with screen integration.

## Features

- **Multi-server support**: Run multiple Minecraft servers independently
- **Screen integration**: Access server console anytime via screen
- **Graceful restarts**: Proper server shutdown handling
- **Auto-recovery**: Cleans up dead screen sessions
- **SystemD native**: Full integration with systemd for logging and management

## Installation

Install from AUR:
```bash
yay -S mc-server-manager-systemd
```

Or manually:
```bash
git clone https://aur.archlinux.org/mc-server-manager-systemd.git
cd mc-server-manager-systemd
makepkg -si
```

## Quick Start

### 1. Prepare Your Server

Create a directory for your server:
```bash
sudo mkdir -p /opt/minecraft-servers/myserver
sudo chown minecraft:minecraft /opt/minecraft-servers/myserver
```

Place your Minecraft server files in the directory and create a `run.sh` script:
```bash
#!/bin/bash
java -Xmx2G -Xms2G -jar server.jar nogui
```

Make it executable:
```bash
sudo chmod +x /opt/minecraft-servers/myserver/run.sh
```

### 2. Start Your Server
```bash
# Start the server
sudo systemctl start minecraft@myserver

# Check status
sudo systemctl status minecraft@myserver

# Enable auto-start on boot
sudo systemctl enable minecraft@myserver
```

### 3. Access Console

Attach to the screen session:
```bash
sudo -u minecraft screen -r myserver-minecraft
```

Alternatively for easier access add an alias:
``` bash
alias mcscreen='sudo -u minecraft screen'
```

Detach without stopping the server: Press `Ctrl+A`, then `D`

## Managing Servers

### Starting/Stopping
```bash
# Start
sudo systemctl start minecraft@servername

# Stop
sudo systemctl stop minecraft@servername

# Restart
sudo systemctl restart minecraft@servername

# Status
sudo systemctl status minecraft@servername
```

### Multiple Servers

Run as many servers as you need:
```bash
sudo systemctl start minecraft@survival
sudo systemctl start minecraft@creative
sudo systemctl start minecraft@modded
```

Each server runs independently in `/opt/minecraft-servers/<name>/`

You can list all running servers using:
```bash
sudo -u minecraft screen -ls
```
Or use the previously established alias:
```bash
mcscreen -ls
```


## Uninstallation

Remove the package:
```bash
sudo pacman -R mc-server-manager-systemd
```

Optionally remove user and data:
```bash
sudo systemctl stop 'minecraft@*'
sudo userdel -r minecraft
sudo rm -rf /opt/minecraft-servers
```

## Contributing

Issues and pull requests welcome at:
https://github.com/Arcticzomb/mc-server-manager-systemd
