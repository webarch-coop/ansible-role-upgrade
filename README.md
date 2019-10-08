# Ansible Debian Upgrade Role 

This repository contains an Ansible role for updating Webarchitects Debian servers.

To use this role you need to use Ansible Galaxy to install it into another repository by adding a `requirements.yml` file in that repo that contains:

```yml
---
- name: upgrade
  src: https://git.coop/webarch/upgrade.git
  version: master
  scm: git
```

To pull this repo in run:

```bash
ansible-galaxy install -r requirements.yml --force
```

The other repo should also contain a `upgrade.yml` file that contains:

```yml
---
- name: Upgrade the Debian servers
  become: yes

  hosts:
    - jessie_servers
    - stretch_servers

  roles:
    - upgrade
```

And a `hosts.yml` file that contains lists of servers, for example:

```yml
---
all:
  children:
    stretch_servers:
      hosts:
        host3.example.org:
        host4.example.org:
        cloud.example.com:
        cloud.example.org:
        cloud.example.net:
    jessie_servers:
      hosts:
        host1.example.org:
        host2.example.org:
```

Then it can be run as follows:

```bash
ansible-playbook upgrade.yml -i hosts.yml
```

You can also limit upgrades to just the Stretch server:

```bash
ansible-playbook upgrade.yml -i hosts.yml --limit="stretch_servers"
```

Or just one server:

```bash
ansible-playbook upgrade.yml -i hosts.yml --limit="host1.example.org"
```

Or use wildcards to match several servers:

```bash
ansible-playbook upgrade.yml -i hosts.yml --limit="cloud*"
```



