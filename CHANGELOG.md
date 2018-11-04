Changelog
=========

1.5.0
-----
* Update apt parameters for Ansible 2.7

1.4.2
-----
* Revert default for automatic non-security updates to `false`

1.4.1
-----
* Change unattended-upgrades email to errors only

1.4.0
-----
* Change default for automatic non-security updates to `true`
* Update unattended-upgrades settings for Buster/Bionic
* Remove unsupported OpenSSH MACs for Buster/Bionic
* Remove apt systemd timer overrides

1.3.1
-----
* Update CPU vendor check for Ansible 2.4
* Bump minimum Ansible version to 2.4

1.3.0
-----
* Add CPU microcode updates
* Add autoupdate package blacklist

1.2.0
-----
* Override apt systemd timer(s) properly

1.1.1
-----
* Combine unattended-upgrades tasks

1.1.0
-----
* No non-security updates by default

1.0.0
-----
* Initial release
