---
context:
  - "[[systemd]]"
  - "[[System Software]]"
---

# systemctl

The primary command-line tool for controlling and interacting with [[systemd]].

---

Basic functionality includes:

- Managing system services (`start`, `stop`, `restart`, `enable`, `disable`)
- Viewing system status
- Managing system power states (shutdown, reboot, suspend)
- Managing units (services, sockets, mounts, devices, etc.)

## Common Commands

### Service Management

- `systemctl start <service>`: Start a service.
- `systemctl stop <service>`: Stop a service.
- `systemctl restart <service>`: Restart a service.
- `systemctl reload <service>`: Reload configuration without interrupting service.
- `systemctl status <service>`: Check service status.
- `systemctl enable <service>`: Enable service to start at boot.
- `systemctl disable <service>`: Disable service from starting at boot.
- `systemctl is-enabled <service>`: Check if service is enabled.

### System State

- `systemctl reboot`: Reboot the system.
- `systemctl poweroff`: Power off the system.
- `systemctl suspend`: Suspend the system.
- `systemctl hibernate`: Hibernate the system.

### System Information

- `systemctl list-units`: List active units.
- `systemctl list-unit-files`: List all installed unit files.
- `systemctl list-dependencies`: Show unit dependencies.
- `systemctl --failed`: List failed units.
