# Peertube Installation
## Requirements
### Ansible node VM
Install ansible in your working directory:
> ⚠️ **Warning**: In my node my user is ansible, you can change it by your user so be careful to check the user you use, I reccomend to use a ansible user.
```bash
sudo apt install python3-pip pipx sshpass python3-passlib
pipx install --include-deps ansible
pipx install ansible-lint # Optional for linting
pipx ensurepath
```
> ⚠️ **Warning**: Think to kill terminal and open a new one to apply changes of pipx ensurepath

The node VM must have a user with sudo privileges and no password prompt for sudo commands.
To do this, add the following line to the sudoers file after running `sudo visudo`:
```bash 
%sudo   ALL=(ALL:ALL) ALL # Add the following line after this one
ansible ALL=(ALL) NOPASSWD: ALL
```
### Client VM Template
add user ansible with sudo privileges:
```bash
sudo adduser ansible
sudo usermod -aG sudo ansible
```
If sudo is not installed, install it:
```bash
sudo apt install sudo
```
The client VM must have a user with sudo privileges and no password prompt for sudo commands.
To do this, add the following line to the sudoers file after running `sudo visudo`:
```bash 
%sudo   ALL=(ALL:ALL) ALL # Add the following line after this one
ansible ALL=(ALL) NOPASSWD: ALL
```
SSH must be installed and the client VM must be accessible from the host VM.
```bash	
sudo apt install openssh-server
```
> ⚠️ **Warning**: You need to know the ip address of the client VM

## Credentials of the project
There is the default credentials of the project. You can change them in the `group_vars/all` file or `group_vars/peertube` file.<br>
Database:
```
database: peertube_prod
user: peertube
password: peertube
```

Ansible user(node):
```
user: ansible
password: ansible
```

Ansible user(client):
```
user: ansible
password: ansible
```

Peertube user:
```
user: peertube
password: peertube
```

## Installation
clone the repository:
```bash
git clone
```

Go to the ansible-peertube directory:
```bash
cd ansible-peertube
```
Put the ip address of the client VM in the inventory file ```hosts.ini```:
```config
[peertube]
peertube1 ansible_host=<ip_address>
```

Run the playbook init and enter the password of the ansible user of the client VM when prompted:
```bash
ansible-playbook playbook-init.yml -k
```

Run the playbook peertube:
```bash
ansible-playbook playbook-peertube.yml
```

## Access to the application
You can access to the application by the ip address of the client VM with your navigator at the following address:
```
https://<ip_address>
```

## Upgrade
To upgrade the application, you can run the playbook peertube with the tag upgrade:
```bash
ansible-playbook playbook-upgrade-peertube.yml
```