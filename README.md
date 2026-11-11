# ids 

A lightweight, real-time Intrusion Detection System (IDS) written in
Python.
Monitors network traffic and alerts on:
- Blacklisted IP connections
- SYN flood attempts
- Port scans

------------------------------------------------------------------------

## Requirements

-   **Python** ≥ 3.10\
-   System: `libpcap-dev`, `tcpdump`, `iptables`
-   Python: `scapy`, `numpy`, `requests`

Supported distros: Ubuntu/Debian, RHEL/CentOS, Fedora, Arch Linux.

------------------------------------------------------------------------

## Quick Install

``` bash
git clone <repo-url>
cd ids 
chmod +x setup.sh
sudo ./setup.sh
```

The script will install dependencies, configure logs, and set up a
systemd service.

------------------------------------------------------------------------

## Usage

### Service

``` bash
sudo systemctl start ids.service
sudo systemctl stop ids.service
sudo systemctl status ids.service
sudo systemctl enable ids.service
```

### Standalone

``` bash
sudo python3 main.py
```

------------------------------------------------------------------------

## Logs

``` bash
journalctl -u ids.service -f      # Service logs
tail -f cz-ids_alerts.log               # Alerts
tail -f /var/log/ids.log               # Output
tail -f /var/log/ids_error.log         # Errors
```

------------------------------------------------------------------------

## Manage / Remove

``` bash
sudo systemctl stop ids.service
sudo systemctl disable ids.service
sudo rm /etc/systemd/system/ids.service
sudo systemctl daemon-reload
```

------------------------------------------------------------------------

## Notes

-   Must run as **root** for packet capture.
-   Default interface can be changed inside `main.py`.
-   Lightweight enough for home labs, servers, or small networks.
