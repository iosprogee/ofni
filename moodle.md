### [moodlebox](https://github.com/moodlebox/moodlebox) 

#### install ansible & [sshpass](https://gist.github.com/arunoda/7790979#installing-on-os-x)
```
    pip3 install ansible
    ansible --version

    brew install https://raw.githubusercontent.com/kadwanev/bigboybrew/master/Library/Formula/sshpass.rb

```
#### list files and folders 
```
   $ gdrive list --query " 'root' in parents"
   $ gdrive list --query " '1xKp1cu7zv7SoZQLj-l_vP-nva0BXajZf' in parents"
```
#### install
```
   $ ~/go/bin/gdrive upload -p 1xKp1cu7zv7SoZQLj-l_vP-nva0BXajZf -r info
```
