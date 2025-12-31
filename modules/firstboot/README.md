# Firstboot Module

Run scripts on first boot and first login.

## Usage

```yaml
modules:
  - type: firstboot
    from: ghcr.io/yourusername/firstboot:latest
    scripts:
      - name: setup-system.sh
        mode: system
        # when: boot (default)
      - name: install-nix.sh
        mode: user
        when: login
```

## Options

### `scripts` (required)
Array of script configurations:

- **`name`** (required): Script filename in `files/firstboot/`
- **`mode`** (optional): `system` (default) or `user`
  - `system`: Runs as root
  - `user`: Runs as each user (UID >= 1000)
- **`when`** (optional): `boot` (default) or `login`
  - `boot`: Runs during system boot
  - `login`: Runs on first graphical login

## Examples

### System Boot Script
```bash
#!/usr/bin/env bash
# Runs as root during boot
echo "System setup complete" > /var/log/firstboot.log
```

### User Login Script  
```bash
#!/usr/bin/env bash
# Runs as each user on first login
mkdir -p "$HOME/.config/myapp"
```

## Notifications

Users receive a desktop notification on first login showing:
- Successful task count
- Failed task count (if any)
- List of failed scripts
