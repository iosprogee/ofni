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
#### [termux services](https://wiki.termux.com/wiki/Termux-services)
```
pkg install termux-api
pkg install termux-services
## restart termux

sv-enable sshd
sv up sshd
sv down sshd
sv status sshd
$PREFIX/bin/service-daemon restart

```

#### ansible install
```

For Python3 and an explanation see [here](https://github.com/nicenemo/termux-setup/blob/master/README.md)
The script used:

#!/data/data/com.termux/files/usr/bin/bash
yes | pkg upgrade  && \
yes | pkg install \
  python \
  python-dev \
  libffi \
  libffi-dev \
  openssl \
  openssl-dev \
  libsodium  \
  clang \
  cmake
# Install the latest Python package manager.
# The version of pip that comes with Python may be outdated.
pip install --upgrade pip 
pip list --outdated --format=freeze | \
  grep -v '^\-e' | \
  cut -d = -f 1 | \
  xargs -n1 pip install -U && \
#  The pynacl dependency originally did not install because
#  it gave problems  building dependencies'
pip install  --upgrade pynacl 
pip install --upgrade ansible
```