# Ansible Role: php
[![CI](https://github.com/msltwtf/ansible-role.php/actions/workflows/ci.yml/badge.svg)](https://github.com/msltwtf/ansible-role.php/actions/workflows/ci.yml)  
Install php and php-modules in a specific version from the sury.org repo.

[Changelog](CHANGELOG.md)

# Requirements

None.

# Role Variables

Available variables are listed below, along with default values from `defaults/main.yml`


## php_version

**WARNING: Required variable without a default value!!!**

```yaml
php_version: ''
```

PHP Version that shall be installed. No default to avoid accidental upgrades.

---

## php_packages

```yaml
php_packages:
  - name: curl
  - name: mysql
  - name: zip
```

This list of packages to install. Each package can be uninstalled individually by adding `state: absent` like in this example.

```yaml
php_packages:
  - name: curl
  - name: mysql
    state: absent
```

php-mysql will be uninstalled in this example.

---

## php_settings

```yaml
php_settings: []
```

Overwrite php settings in the php.ini config files. Overwrites are defined in key value format like below.

```yaml
php_settings:
  php_file_uploads: "On"
  php_date_timezone: "Europe/Berlin"
```

---

# Dependencies

None.

# Example Playbook

```yaml
- hosts: all
  vars:
    php_version: '8.2'
    php_packages:
      - name: curl
      - name: mysql
      - name: pdo
        state: absent
  roles:
    - msltwtf.php
```

# License

MIT
