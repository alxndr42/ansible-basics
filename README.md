# ansible-basics

Basic setup for Debian-based systems with systemd.

This role installs (among other things) an improved SSH configuration (i.e.
public key login only, secure algorithms) and configures unattended upgrades.
Security updates provided by the distribution will always be installed,
non-security updates can optionally be allowed.

## Role Variables

Please see [defaults/main.yml](defaults/main.yml) for default values.

| Variable | Description |
| --- | --- |
| `basics_autoupdate_blacklist` | List of packages that must not be automatically updated. |
| `basics_autoupdate_mail` | Email address to send unattended upgrade errors to. |
| `basics_autoupdate_non_security` | Install non-security updates provided by the distribution. |
| `basics_autoupdate_origins` | Additional list of `Origins-Pattern` values. |
| `basics_autoupdate_reboot` | Allow automatic reboots for unattended upgrades. This is either `true` or `false` as a string value. |
| `basics_autoupdate_update_calendar` | `OnCalendar` value for *apt-daily.timer*. |
| `basics_autoupdate_update_delay` | `RandomizedDelaySec` value for *apt-daily.timer*. |
| `basics_autoupdate_upgrade_calendar` | `OnCalendar` value for *apt-daily-upgrade.timer*. |
| `basics_autoupdate_upgrade_delay` | `RandomizedDelaySec` value for *apt-daily-upgrade.timer*. |
| `basics_history_disabled` | Disable persistent history in Bash etc. |
| `basics_journald_maxfile` | *journald.conf* `MaxFileSec` override. |
| `basics_journald_maxretention` | *journald.conf* `MaxRetentionSec` override. |
| `basics_journald_storage` | *journald.conf* `Storage` override. |
| `basics_microcode_updates` | Install CPU microcode updates. |
| `basics_packages_install` | List of packages that are always installed. |
| `basics_packages_remove` | List of packages that are always removed. |
| `basics_services_disable` | List of services that are always disabled. |
| `basics_ssh_listen` | Values of `ListenAddress` for *sshd_config*. |
| `basics_ssh_match_blocks` | List of `Match` blocks for *sshd_config* (see below). |
| `basics_ssh_port` | Value of `Port` for *sshd_config*. |
| `basics_ssh_root_login` | Value of `PermitRootLogin` for *sshd_config*. |
| `basics_ufw_allow` | List of UFW `allow` rules (see below). |
| `basics_ufw_deny` | List of UFW `deny` rules (see below). |
| `basics_ufw_ssh` | Allow SSH as the first UFW rule. |
| `basics_ufw` | Configure and enable UFW. |

## SSH Match Blocks

Example `Match` block configuration:

```yaml
basics_ssh_match_blocks:
  - match: User sftpuser
    options:
      - ForceCommand internal-sftp
```

Resulting entry in *sshd_config*:

```
Match User sftpuser
  ForceCommand internal-sftp
```

## UFW Rules

Example UFW rules:

```yaml
- port: "80,443"
  proto: tcp

- src: "192.168.0.42"
  src_port: 1234
  dst: "192.168.0.1"
  port: 53
  proto: udp
  interface: eth0
  direction: in
```

## License

GNU General Public License v3 or later (GPLv3+)
