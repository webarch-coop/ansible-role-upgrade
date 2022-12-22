# Webarchitects Ansible Debian update and upgrade Role 

[![pipeline status](https://git.coop/webarch/upgrade/badges/master/pipeline.svg)](https://git.coop/webarch/upgrade/-/commits/master)

This repository contains an Ansible role for updating Debian servers.

## Dependencies

This role includes the following Webarchitects roles:

* [apt](https://git.coop/webarch/apt)

## Role variables

See the [defaults/main.yml](defaults/main.yml) file for the default variables and [meta/argument_spacs.yml](meta/argument_specs.yml) for the variable specification.

### upgrade

If `upgrade` is `true` tasks in this role will be run, set it to `false` for servers that should not be upgraded using Ansible, it defaults to `true`.

### upgrade_apticron

If `upgrade_apticron` is `true` a MTA will be installedi for `apticron`, this needs to be false for servere that already have a MTA listening on a SMTP port. It defaults to `false`.

## upgrade_chroot

A path to a chroot that should be upgraded, if the path doesn't exist these tasks will be skipped, `upgrade_chroot` defaults to `/chroot`.

## Repository

The primary URL of this repo is [`https://git.coop/webarch/upgrade`](https://git.coop/webarch/upgrade) however it is also [mirrored to GitHub](https://github.com/webarch-coop/ansible-role-upgrade) and [available via Ansible Galaxy](https://galaxy.ansible.com/chriscroome/upgrade).

If you use this role please use a tagged release, see [the release notes](https://git.coop/webarch/upgrade/-/releases).

## License

This role is released under [the same terms as Ansible itself](https://github.com/ansible/ansible/blob/devel/COPYING), the [GNU GPLv3](LICENSE).
