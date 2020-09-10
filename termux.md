#### diable welcome termux
```
 touch ~/.hushlogin
```
#### [gdrive cli]()
```
```
#### localtunnel
```
 npm i -g localtunnel-termux
 lt -v
 lt -p 8888 -s gatoree
```
#### ssh
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

 - edit sshd config
 $ nano $PREFIX/etc/ssh/sshd_config
   
```
#### [termux keys](https://wiki.termux.com/wiki/Touch_Keyboard)
```
 Volume Up+X → Alt+X
 Volume Up+W → Up arrow key
 Volume Up+A → Left arrow key
 Volume Up+S → Down arrow key
```
#### [termux services](https://wiki.termux.com/wiki/Termux-services)
```
 pkg install termux-api
 pkg install termux-services

 sv-enable sshd
 sv up sshd
 sv status sshd
 $PREFIX/bin/service-daemon restart
```
#### remove service
```
 sv down telnetd
 sv-enable telnetd
 rm -rf $PREFIX/var/service/telnetd
```
### ENV
```
 echo $HOME
 /data/data/com.termux/files/home
 echo $PREFIX
 /data/data/com.termux/files/usr
```
#### [tor chat](https://medium.com/alize-in-cryptoland/how-to-run-a-secure-chat-behind-tor-off-of-your-android-phone-be83a678693d)
```
 pkg install tor
 pkg install torsocks

 nano $PREFIX/etc/tor/torrc
   ## Enable TOR SOCKS proxy
   SOCKSPort 127.0.0.1:9050

   ## Hidden Service: SSH
   HiddenServiceDir /data/data/com.termux/files/home/.tor/hidden_ssh
   HiddenServicePort 22 127.0.0.1:8022

   ## Hidden Service: CryptoChat
   HiddenServiceDir /data/data/com.termux/files/home/.tor/hidden_ssh
   HiddenServicePort 3000 127.0.0.1:80

 mkdir -p ~/.tor/hidden_ssh

 tor
 cat ~/.tor/hidden_ssh/hostname

 accessing
 torsocks ssh -p pfaojfzcqbavxtoy2pbwr3ymcotjdxqscf47lc4x25m4oi3kqesoflad.onion
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