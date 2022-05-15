# Changelog

## 1.11.0

- Add new `Origins-Pattern` for Debian security updates
- Change `basics_autoupdate_reboot` to boolean
- Replace `include` with `include_tasks`

## 1.10.0

- Add `basics_ssh_listen`/`basics_ssh_port` variables
- Add variables for apt-daily/-upgrade timer overrides

## 1.9.0

- Add `basics_history_disabled` variable
- Add `basics_ssh_root_login` variable

## 1.8.0

- Add UFW deny rules, support more parameters

## 1.7.0

- Add UFW configuration

## 1.6.0

- Add journald.conf retention overrides

## 1.5.3

- Remove `basics_autoupdate_reboot_time` variable

## 1.5.2

- Remove custom python-apt installation
- Distribution fallback if `ansible_lsb` is empty

## 1.5.1

- Fix Ansible deprecation warning

## 1.5.0

- Update apt parameters for Ansible 2.7

## 1.4.2

- Revert default for automatic non-security updates to `false`

## 1.4.1

- Change unattended-upgrades email to errors only

## 1.4.0

- Change default for automatic non-security updates to `true`
- Update unattended-upgrades settings for Buster/Bionic
- Remove unsupported OpenSSH MACs for Buster/Bionic
- Remove apt systemd timer overrides

## 1.3.1

- Update CPU vendor check for Ansible 2.4
- Bump minimum Ansible version to 2.4

## 1.3.0

- Add CPU microcode updates
- Add autoupdate package blacklist

## 1.2.0

- Override apt systemd timer(s) properly

## 1.1.1

- Combine unattended-upgrades tasks

## 1.1.0

- No non-security updates by default

## 1.0.0

- Initial release
