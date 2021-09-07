ansible-basics
==============

Basic setup for Debian-based systems.

This role installs (among other things) an improved SSH configuration
(i.e. public key login only, secure algorithms) and configures unattended
upgrades. Security updates provided by the distribution will always be
installed, non-security updates can optionally be allowed.

Role Variables
--------------

Please see [defaults/main.yml](defaults/main.yml) for default values.

<table>
<tr>
  <th>Variable</th>
  <th>Description</th>
</tr>
<tr>
  <td>basics_autoupdate_blacklist</td>
  <td>List of packages that must not be automatically updated.</td>
</tr>
<tr>
  <td>basics_autoupdate_mail</td>
  <td>Email address to send unattended upgrade errors to.</td>
</tr>
<tr>
  <td>basics_autoupdate_non_security</td>
  <td>Install non-security updates provided by the distribution.</td>
</tr>
<tr>
  <td>basics_autoupdate_origins</td>
  <td>Additional list of <tt>Origins-Pattern</tt> values.</td>
</tr>
<tr>
  <td>basics_autoupdate_reboot</td>
  <td>
    Allow automatic reboots for unattended upgrades.
    This is either <tt>true</tt> or <tt>false</tt> as a string value.
  </td>
</tr>
<tr>
  <td>basics_history_disabled</td>
  <td>Disable persistent history in Bash etc.</td>
</tr>
<tr>
  <td>basics_journald_maxfile</td>
  <td>journald.conf <tt>MaxFileSec</tt> override.</td>
</tr>
<tr>
  <td>basics_journald_maxretention</td>
  <td>journald.conf <tt>MaxRetentionSec</tt> override.</td>
</tr>
<tr>
  <td>basics_journald_storage</td>
  <td>journald.conf <tt>Storage</tt> override.</td>
</tr>
<tr>
  <td>basics_microcode_updates</td>
  <td>Install CPU microcode updates.</td>
</tr>
<tr>
  <td>basics_packages_install</td>
  <td>List of packages that are always installed.</td>
</tr>
<tr>
  <td>basics_packages_remove</td>
  <td>List of packages that are always removed.</td>
</tr>
<tr>
  <td>basics_services_disable</td>
  <td>List of services that are always disabled.</td>
</tr>
<tr>
  <td>basics_ssh_match_blocks</td>
  <td>List of <tt>Match</tt> blocks for <i>sshd_config</i> (see below).</td>
</tr>
<tr>
  <td>basics_ssh_root_login</td>
  <td>Value of <tt>PermitRootLogin</tt> for <i>sshd_config</i>.</td>
</tr>
<tr>
  <td>basics_ufw</td>
  <td>Configure and enable UFW.</td>
</tr>
<tr>
  <td>basics_ufw_allow</td>
  <td>List of UFW <tt>allow</tt> rules (see below).</td>
</tr>
<tr>
  <td>basics_ufw_deny</td>
  <td>List of UFW <tt>deny</tt> rules (see below).</td>
</tr>
<tr>
  <td>basics_ufw_ssh</td>
  <td>Allow SSH as the first UFW rule.</td>
</tr>
</table>

SSH Match Blocks
----------------

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

UFW Rules
---------

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

License
-------

GPLv3
