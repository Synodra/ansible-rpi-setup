# ansible-rpi-setup

This repo contains an Ansible playbook aiming to automate the configuration of my raspberri PIs.

## How to use this ansible script

- Make a new Raspberry PI sd card ready using pi-utils
- Insert the sd card & power the Raspberry PIs
- Clone this repo
- Personalized `config.yaml` & `inventories.yaml` using default file
- Launch the Ansible script : `ansible-playbook playbook.yaml -i inventories.yaml --ask-become-pass`



## Other informations

### Testing the Playbook

The Ansible playbook can be tested with a dry run using this command : `ansible-playbook playbook.yaml -i inventories.yaml --ask-become-pass --check`.

### Set up ansible user w/ shell

``` shell
useradd -rm ansible
echo "ansible ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/ansible
chmod 440 /etc/sudoers.d/ansible
mkdir -m 700 /home/ansible/.ssh
echo "ssh-ed25519 blablablalapookiedanslesas ansible" > /home/ansible/.ssh/authorized_keys
chmod 600 /home/ansible/.ssh/authorized_keys
chown -R ansible.ansible /home/ansible/.ssh
```
