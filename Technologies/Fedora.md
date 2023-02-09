# Fedora 37

## Adding a new sudo user
* Add a new user:
```bash
useradd -G wheel -m -U LOGIN
passwd LOGIN
```
* Run visudo and uncomment:
```bash
visudo
...
%wheel ALL=(ALL) ALL
...
```

## Changing SSH port & removing root logins
* edit /etc/ssh/sshd_config
* Uncomment line with Port 22 and change port to desired port
* SELinux has to know about this change:
```
semanage port -a -t ssh_port_t -p tcp PORTNUMBER
```
* Change port of SSH service for firewalld (/usr/lib/firewalld/services/ssh.xml) and restart
firewall with firewalld --reload
* Change "PermitRootLogin yes" to "no"
* Restart sshd

## Setup SSH key instead of passwords
* Create key with ssh-keygen
```
ssh-keygen -o -t rsa -b 4096 -C "miracle@dreamsmith.net"
```
* Check if key was created and see if it is of the right type and bit size
```
ssh-keygen -l -f .ssh/id_rsa
```
* Copy the key using ssh-copy-id
```
ssh-copy-id -i .ssh/id_rsa.pub user@ip
```
* Or copy manually
```
ssh username@remote-system
mkdir ~/.ssh
chmod 700 ~/.ssh
edit ~/.ssh/authorized_keys and copy the public key
chmod 600 ~/.ssh/authorized_keys
```
* Disable PasswordAuthentication in /etc/ssh/sshd_config:
```
PasswordAuthentication no
ChallengeResponseAuthentication no
```
