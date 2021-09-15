
# Learn Ansible
This repository is used by me to learn ansible to setup nginx web server

### Environment
- Ubuntu 20.04
- ansible-playbook 2.9.17
- CentOS 7 (Remote Server)

### Setup for Remote Server
Before we can play the cofniguration, we need to add our host (IP address and the alias) to `/etc/ansible/hosts`

*in my case, I name it remoteserver, so I add this to the last line of `/etc/ansible/hosts` file*
```
[remoteserver]
<remote-server-ip>
```

To check if the host is configured properly, we can test by executing command
```
$ ansible remoteserver -m ping
-- the output will be --

<server-ip-address> | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}

```
### Executing
---
#### For localhost
```
$ ansible-playbook nginx-playbook.yml -K

or

$ ansible-playbook nginx-playbook.yml --ask-become-pass
```
**note that we will be prompted to enter our sudoers password, since we need permission to perform installation*

#### for Remote Server
```
$ ansible-playbook remotely/nginx-playbook.yml
```
**make sure you have your public key on the remote server*