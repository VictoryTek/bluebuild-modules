# BlueBuild Modules

Custom modules for [BlueBuild](https://blue-build.org/).

## Available Modules

### Firstboot Module

Run scripts on first boot and first login with desktop notifications.

[Documentation](./modules/firstboot/README.md)

**Usage:**
```yaml
- type: firstboot
  from: ghcr.io/yourusername/firstboot:latest
  scripts:
    - name: setup.sh
      mode: system
    - name: install-nix.sh
      mode: user
      when: login
```

## License

Apache 2.0
