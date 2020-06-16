### [google console](https://ssh.cloud.google.com/cloudshell/editor)
#### debian 9
```
  $ cat /etc/os-release
```
#### make installation persistent [ref](https://cloud.google.com/shell/docs/configuring-cloud-shell#environment_customization_script)
```
  $ nano $HOME/.customize_environment
```
```
		#!/bin/sh
		apt-get update
		apt-get -y install erlang
```
#### install apache2 php7
```
  $ sudo apt install apache2 php libapache2-mod-php php-pspell php-curl php-gd php-intl -y
  $ sudo apt install php-xml php-xmlrpc php-ldap php-zip php-soap php-mbstring -y
  $ sudo apt install mariadb-server php-mysql -y
  $ sudo service apache2 restart
```
#### change port to 8080
```
  $ sudo nano /etc/apache2/ports.conf 
```
>>  `Listen 80 `  change to  `Listen 8080`
#### start apache2 service
```
  $ sudo service apache2 start
```
#### view the webservice 
- click on web preview
<div style="height=40px;width: 40px;line-height: 28px;">
<svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" class="ng-star-inserted"><path d="M20 4c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2 V6c0-1.1.9-2 2-2h16zm0 14V8H4v10h16zm-8-9l7 4-7 4-7-4 7-4zm0 5.9c1 0 1.9-.8 1.9-1.9 0-1.1-.8-1.9-1.9-1.9-1.1 0-1.9.8-1.9 1.9 0 1.1.9 1.9 1.9 1.9z"></path></svg>
</div>    
- preview on port 8080


#### create index.php
```
  $ cd /var/www/html/
  $ sudo rm index.html  
  $ sudo nano index.php
```
> ```
>    <?
>      phpinfo();
>    ?>
> ```
>> ```
>>   
>>   $ sudo service apache2 restart
>>   $ sudo service mysql start
>>   $ sudo mysql_secure_installation
>> ```

```
grep -rn /etc/apache2/ -e "ServerName"

cat  /etc/apache2/ports.conf | grep Listen
```
