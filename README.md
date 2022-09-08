# ansible-rpi-setup

Ansible playbook aiming to automate the configuration of my rpi homalab.

## How to use this ansible script

- Format sd card using raspberry pi utils
- Power the raspberry
- Add the raspberry pi to the inventory file
- Launch the ansible script to setup the raspberry

### Launch the playbook

The playbook can be launch with the following command :

```bash
ansible-playbook playbook.yml -i inventories
```

### Launch a dry run of this playbook

```bash
ansible-playbook playbook.yml -l thor -i inventories --check
```

## Other informations

### Command to verify host file

```bash
ansible-inventory --list -i hosts -y
```

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
