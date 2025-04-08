# Webarchitects Ansible Debian update and upgrade role

[![pipeline status](https://git.coop/webarch/upgrade/badges/master/pipeline.svg)](https://git.coop/webarch/upgrade/-/commits/master)

This repository contains an Ansible role for updating Debian servers.

## Role variables

See the [defaults/main.yml](defaults/main.yml) file for the default variables and [meta/argument_spacs.yml](meta/argument_specs.yml) for the variable specification.

### upgrade

If `upgrade` is `true` tasks in this role will be run, set it to `false` for servers that should not be upgraded using Ansible, it defaults to `true`.

### upgrade_changelog

When `true` white a `/root/Changelog` with the list of packages installed, it defaults to `true`.

### upgrade_chroot

A path to a chroot that should be upgraded, if the path doesn't exist these tasks will be skipped, `upgrade_chroot` defaults to `/chroot`.

### upgrade_reboot

A boolean, reboot the server when the `NEEDRESTART-KSTA` variable returned from `needrestart -b` is `"3"` and `upgrade_reboot` is `true`, it defaults to `false`.

### upgrade_restart

A boolean, restart systemd services when then are listed by `needrestart -b`, `upgrade_restart` defaults to `true`, set it to `false` to totally skip restarting services.

### upgrade_restart_skip

A list of names of services that should not be restated, by default `upgrade_restart_skip` is a list containing only one service, `dbus.service`, set to `[]` if no services should be skipped.

### upgrade_restart_skip_regex

A regular expression to match names of services that should not be restated, by default `upgrade_restart_skip_regex` is iset to `^valkey-.*`, set to `""` if no services should be skipped.

## Notes

If a apt repo is down this role will fail, in this case you can uypdate servers like this:

```bash
ansible example.org -m ansible.builtin.shell -a "sudo apt update && sudo DEBIAN_FRONTEND=noninteractive apt full-upgrade -y"
```

## Repository

The primary URL of this repo is [`https://git.coop/webarch/upgrade`](https://git.coop/webarch/upgrade) however it is also [mirrored to GitHub](https://github.com/webarch-coop/ansible-role-upgrade) and [available via Ansible Galaxy](https://galaxy.ansible.com/chriscroome/upgrade).

If you use this role please use a tagged release, see [the release notes](https://git.coop/webarch/upgrade/-/releases).

## Copyright

Copyright 2018-2025 Chris Croome, &lt;[chris@webarchitects.co.uk](mailto:chris@webarchitects.co.uk)&gt;.

This role is released under [the same terms as Ansible itself](https://github.com/ansible/ansible/blob/devel/COPYING), the [GNU GPLv3](LICENSE).
