#### install 
```
brew cask install virtualbox
brew cask install virtualbox-extension-pack 
brew cask install vagrant
```

#### update 
```
brew cask reinstall virtualbox
brew cask reinstall virtualbox-extension-pack 
brew cask reinstall vagrant
vagrant plugin update
```

#### Vagrantfile 
```
Vagrant.configure("2") do |config|
  config.vm.box = "minimal/centos7"
  config.vm.box_version = "7.0"

  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.network "private_network", ip: "192.168.56.50"

  # config.vm.network "public_network"
  # config.vm.synced_folder "../data", "/vagrant_data"

end


```

