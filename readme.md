# Peertube Installation
## Requirements
### Ansible
Install ansible in your working directory:
```bash
sudo apt install python3-pip pipx sshpass
pipx install --include-deps ansible
pipx install ansible-lint # Optional for linting
pipx ensurepath
```
> ⚠️ **Warning**: Think to kill terminal and open a new one to apply changes of pipx ensurepath

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
Database:
```
database: peertube
user: peertube
password: peertube
```

Ansible user:
```
user: ansible
password: ansible
```

Peertube user:
```
user: peertube
password: peertube
```