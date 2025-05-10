# Ansible Role: PHP

This role installs and configures PHP on various Linux distributions (Debian/Ubuntu, RHEL, Arch Linux).

## Requirements

None.

## Role Variables

```yaml
php_modules: []               # List of PHP modules to install
php_version: "8.1"            # Used on RHEL-based systems
php_memory_limit: "128M"      # Memory limit to set in php.ini
php_ini_path: "/etc/php.ini"  # Path to php.ini (override per system if needed)
```

## Example Playbook

```yaml
- hosts: webservers
  roles:
    - role: php
      vars:
        php_modules:
          - php-mysql
          - php-gd
        php_memory_limit: "256M"
```

## Supported Platforms

- Debian
- Ubuntu
- RHEL / CentOS / Rocky
- Arch Linux

## License

MIT

## Author Information

Created by Dmitry Borovik

