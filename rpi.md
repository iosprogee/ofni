#### update | upgrade
   `$ sudo apt update && sudo apt upgrade -y`

#### [ssh on USB](https://desertbot.io/blog/ssh-into-pi-zero-over-usb)
>**enable ssh on rpi**
> - `$ touch /Volumes/boot/ssh`
> - `$ nano /Volumes/boot/config.txt ` 
> - append at the bottom
>   `dtoverlay = dwc2`
> - `$ nano /Volumes/boot/cmdline.txt`
> - after "rootwait" add:
>   `modules-load=dwc2,g_ether`    
>   **add @ end of line**   
>      `ip=192.168.1.100 `   **works only if eth connection**    
>   **change root=&lt;/dev/device &gt; (note: partition created via fdisk & dd)** [link](https://www.raspberrypi.org/forums/viewtopic.php?t=105868#p1432542)    
>       `root=/dev/mmcblk0p4`

> - **reboot and login over usb**
> ```
>   ssh pi@raspberrypi.local  _(psswd:raspberry)_
>   ssh pi@rpi0w1.local (192.168.1.10)
>   ssh pi@rpi1a.local
> ```

---

#### [configure wifi](https://)
> - `nano /Volumes/boot/wpa_supplicant.conf`
>
> ```
>   ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
>   update_config=1
>   country=PH
>   network={
>	    ssid="1XOXO"
>     psk="Youc@nnot"
>   }
> ```

---

#### [install lamp](https://randomnerdtutorials.com/raspberry-pi-apache-mysql-php-lamp-server/)
> - **apache2**
>
> ```
>   $ sudo apt install apache2 -y
> ```
> - **php**
>
> ```
>   $ sudo apt install php -y
>   $ sudo apt-get install php libapache2-mod-php php-pspell php-curl php-gd php-intl -y
>   $ sudo apt install php-xml php-xmlrpc php-ldap php-zip php-soap php-mbstring -y
> ```
> ```
>   $ cd /var/www/html
>   $ sudo rm index.html
>   $ sudo nano index.php
> ```
> ```
>    <?
>      phpinfo();
>    ?>
> ```
> ```
>   $ sudo service apache2 restart
> ```
> - **mysql**
>
> ```
>   $ sudo apt install mariadb-server php-mysql -y
>   $ sudo service apache2 restart
>   $ sudo mysql_secure_installation
> ```
>   **login to mysql**
> ```
>   $ sudo mysql -u root -p
> ```
>   **run the following**
> ```
>   create user admin@localhost identified by 'passwd';
>   grant all privileges on *.* to admin@localhost;
>   FLUSH PRIVILEGES;
>   select user,host from mysql.user;
>   exit;
> ```

>   **check apache port**
> ```
>   $ cat /etc/apache2/ports.conf | grep Listen
> ```

>   **check apache ServerName**
> ```
>   $ grep -rn /etc/apache2/ -e ServerName
> ```

>   **mariadb config**
> ```
>   $ sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf
> ```
>   **download moodle**
> ```
>   wget https://download.moodle.org/stable38/moodle-latest-38.tgz
>   tar xzf moodle-latest-38.tgz
>   sudo mv moodle /var/www
> ```
>   **create moodle database**
> ```
>   mysql -u root -p
> ```
> ```
>   CREATE DATABASE moodle CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
>   DROP USER admin@localhost;
>   CREATE USER admin@localhost identified by 'Moodlebox4$';
>   GRANT ALL PRIVILEGES on moodle.* to admin@localhost;
>   FLUSH PRIVILEGES;
>   SHOW VARIABLES like 'socket';
>   SHOW VARIABLES like 'port';
> ```

>   **set moodle apache config**
> ```
>   $ sudo nano /etc/apache2/sites-available/000-default.conf
> ```
> ```
>  <VirtualHost *:80>
>    DocumentRoot /var/www/moodle 
>    #Alias /moodle /var/www/moodle 
>    <Directory /var/www/moodle> 
>      Options Indexes FollowSymLinks 
>      AllowOverride All 
>      Require all granted 
>    </Directory>
>    ErrorLog ${APACHE_LOG_DIR}/error.log 
>    CustomLog ${APACHE_LOG_DIR}/access.log combined
>  </VirtualHost>
> ```
>   **restart apache**
> ```
>   $ sudo service apache2 restart
> ```
>   **set moodle www folder permissions**
> ```
>    sudo chown -R www-data:www-data /var/www/moodle
>    sudo chmod -R 755 /var/www/moodle
>    sudo mkdir /var/www/moodledata
>    sudo chown www-data:www-data /var/www/moodledata
>    sudo chmod 755 /var/www/moodledata
> ```

nano /etc/php/7.3/apache2/php.ini
```
    memory_limit = 40M
    post_max_size = 80M
    upload_max_filesize = 80M
```
#### [change password, maintainance mode, etc](https://docs.moodle.org/38/en/Administration_via_command_line#Reset_user_password)

