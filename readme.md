# Peertube Installation
## Requirements
Install ansible in your working directory:
```bash
sudo apt install python3-pip pipx sshpass
pipx install --include-deps ansible
pipx install ansible-lint
pipx ensurepath
```

## Credentials
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