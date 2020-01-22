# maxmind-geoipupdate - Ansible role for Maxmind geoipupdate package

This role installs and configures geoipupdate package. Currently supported
only geoipupdate <= 3.1.1

## Example Playbook

```
---
- hosts: all
  sudo: yes
  roles:
    - { role: maxmind-geoipupdate }
  vars:
    maxmind_settings_AccoundId: '999999'
    maxmind_settings_LicenseKey: '000000000000'
```

## Supported variables

```
# Package to install (RHEL/CentOS/OEL etc)
maxmind_package_el: 'geoipupdate'
# Path to configuration file
maxmind_filename: '/etc/GeoIP.conf'
# Path to binary
maxmind_binary: '/usr/bin/geoipupdate'

## Required settings
# Please note, since 30.12.2019 Maxmind requires valid AccountId / LicenseKey
# They can be obtained from https://www.maxmind.com/en/home
# See https://blog.maxmind.com/2019/12/18/significant-changes-to-accessing-and-using-geolite2-databases/
# Your MaxMind account ID (UserId in geoipupdate <= 2.5).
maxmind_settings_AccountID: '999999'
# Your case-sensitive MaxMind license key.
maxmind_settings_LicenseKey: '000000000000'
# List of database edition IDs (ProductIds in geoipupdate <= 2.5). Edition IDs 
# may consist of letters, digits, and dashes (e.g., "GeoIP2-City", "106").
maxmind_settings_EditionIDs:
  - 'GeoLite2-ASN'
  - 'GeoLite2-City'
  - 'GeoLite2-Country'

## Optional settings

# The directory to store the database files. The default is /usr/share/GeoIP
maxmind_settings_DatabaseDirectory: ''
# The host name of the server to use. The default is updates.maxmind.com.
maxmind_settings_Host: ''
# The proxy host name or IP address. You may optionally specify a port number,
# e.g., 127.0.0.1:8888. If no port number is specified, 1080 will be used.
maxmind_settings_Proxy: ''
# The proxy user name and password, separated by a colon. For instance,
# username:password.
maxmind_settings_ProxyUserPassword: ''
# Whether to preserve modification times of files downloaded from the server.
# This option is either 0 or 1. The default is 0.
maxmind_settings_PreserveFileTimes: ''
# The lock file to use. This ensures only one geoipupdate process can run at a
# time. The default is .geoipupdate.lock under the DatabaseDirectory.
maxmind_settings_LockFile: ''
```

## License
Licensed under MIT

Copyright (c) 2020 Azamat H. Hackimov <azamat.hackimov@gmail.com>

