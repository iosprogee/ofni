#### [gdrive]() - gdrive cli

#### install
```
 $ pkg update
 $ pkg install openssh
 - on termux generate mobile device key
 $ ssh-keygen -t rsa -b 2048 -f id_rsa
 $ cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
 $ chmod 600 ~/.ssh/authorized_keys
 $ chmod 700 ~/.ssh

 - copy id_rsa to gdrive
 - on pc copy id_rsa from gdrive
 $ chmod 600 id_rsa
 $ ssh -i id_rsa -p 8022 term@<ipaddress>
 

```
