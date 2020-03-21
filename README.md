# Ansible Deloy Script for ISLE

This is a starter deploy script for ISLE Host servers. This will not work out of the box and requires modifications for deploy to either remote servers or a local vagrant / VM.

This scripts assumes familiarity and knowledge of Ansible.

## Documentation
Please use the [ISLE Documentation](https://islandora-collaboration-group.github.io/ISLE) for using ISLE to install Islandora on server environments.

### Control Node Requirements

From Ansible documentation:

```bash
Currently Ansible can be run from any machine with Python 2 (version 2.7) or Python 3 (versions 3.5 and higher) installed. This includes Red Hat, Debian, CentOS, macOS, any of the BSDs, and so on. Windows is **not** supported for the control node.
```

* [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) `2.5.1+`
* Git `2.0+`

### Target Requirements

This means the remote server or local vagrant or virtual machine (vm).

* Python 2 or 3 installed
* Is running
* Is accessible by port 22 / ssh
  * Remote Servers: Has the deploy users ssh keys added to `authorized_hosts`
  * Vagrant boxes: use the `~/.vagrant.d/insecure_private_key`
* This playbook can be used on either Ubuntu or CentOS target systems

### This playbook performs or installs the following on Ansible targets (remote servers or local vms)

* Installs dependencies including ntp, openssh, rsync, curl, wget, vim, zip, unzip, nano, emacs25, htop etc.
* Git `2.0+`
* Docker-CE or EE version `19.03.x`+
* [Docker-compose](https://docs.docker.com/compose/install/) version `1.25.4`+
* Creates an `islandora` deploy user with the UID / GUID of `10000` and passwordless sudo rights.
* (optional)
  * Can clone the ISLE project with ISLE images tagged at: `1.4.2`

### Quick Start

* Copy and modify either the `localhost.yml` (use for local vagrant hosts) or `remote-server.yml` (use for remote servers) within the `host_vars` directory
  * Rename to the appropriate host name as needed.
* Update the `inventory` file with the appropriate host name and associated ansible_ssh connectivity parameters.
* Edit the `playbook.yml` file with the appropriate host name
* Test your connection (if the local vm or remote server is running and accessible by port 22 / ssh) open up a terminal and enter the following:
  * `ansible -i inventory -m ping hostname`
* To run the playbook, open up a terminal and enter the following:
  * `ansible-playbook -i inventory playbook.yml`

## Maintainers
* Gavin Morris, Born-Digital
* Mark Sandford, Colgate University
* David Keiser-Clark, Williams College

## Former Contributors
* Francesca Baird, Wesleyan University
* Carolyn Moritz, Vassar College
* Benjamin Rosner (Lead Maintainer 2018-19), Barnard College
* Bethany Seeger (Lead Maintainer 2019), Amherst College
* Shaun Trujillo, Mount Holyoke College
* Steve Young, Hamilton College

## Contributing to ISLE
* [Islandora ISLE Interest Group](https://github.com/islandora-interest-groups/Islandora-ISLE-Interest-Group) - Meetings open to everybody! [Schedule](https://github.com/islandora-interest-groups/Islandora-ISLE-Interest-Group/#how-to-join) is alternating Wednesdays, 3:00pm EDT
* [Islandora ISLE Google group](https://groups.google.com/forum/#!forum/islandora-isle) - Post your questions here and subscribe for updates, meeting announcements, and technical support
