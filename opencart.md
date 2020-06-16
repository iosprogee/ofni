
#### install nginx php
```
sudo apt install nginx
sudo apt-get install php7.3-cli php7.3-fpm php7.3-curl php7.3-gd php7.3-mysql php7.3-mbstring zip unzip
sudo apt install php7.3-opcache php7.3-gd  php7.3-intl php7.3-xsl php7.3-zip php7.3-bcmath php7.3-soap

sudo nano /etc/php/7.3/fpm/php.ini
```
```  
Change the following lines:
  memory_limit = 256M
  upload_max_filesize = 100M
  opcache.save_comments=1
  max_execution_time = 300
  date.timezone = Asia/Manila
```

#### install mysql-server
```  
sudo apt-get install mysql-server
```

####  WSL disable Linux Native AIO by setting innodb_use_native_aio = 0  my.cnf
```
  sudo nano /etc/mysql/conf.d/mysql-fix.cnf
    [mysqld]
    innodb_use_native_aio = 0
```

#### mysql -u root -p
```
  > CREATE DATABASE opencartdb;
  > GRANT ALL ON opencartdb.* TO 'opencart'@'localhost' IDENTIFIED BY '0p3nC@rt7';
```

#### gcloud mysql closecart   
```
  > CREATE DATABASE closecartdb;
  > GRANT ALL ON closecartdb.* TO 'closecart'@'%' IDENTIFIED BY '0p3nC@rt7';
  > DROP USER 'closecart'@'*'

  > FLUSH PRIVILEGES;
  > EXIT;

  > USE mysql;
  > SELECT host,name FROM user;
  
  # change opencart db main user password
  >  ALTER USER 'opencart'@'localhost' IDENTIFIED BY 'opencart1103';  
  # change opencart admin password
  >  UPDATE `oc_user` set `password` = sha1( concat(`salt`, sha1( concat(`salt`, sha1('opencart1103'))))) WHERE user_id = 1
```

#### download OpenCart(https://www.howtoforge.com/how-to-install-opencart-on-debian-10/)
```
  wget --no-hsts https://github.com/opencart/opencart/releases/download/3.0.3.3/opencart-3.0.3.3.zip
  unzip opencart-3.0.3.3.zip
  mv upload /var/www/html/opencart


  cd /var/www/html/opencart/
  mv config-dist.php config.php
  mv admin/config-dist.php admin/config.php

  sudo chown -R www-data:www-data /var/www/html/opencart/
  sudo chmod -R 775 /var/www/html/opencart/
```

#### nano /etc/nginx/sites-available/opencart.conf
```
  server {
    #listen 80;
    #server_name opencart.linuxbuz.com;

    listen 80 default_server;
    listen [::]:80 default_server;

    root /var/www/html/opencart;
    index index.php;

    server_name _;

    access_log /var/log/nginx/opencart_access.log;
    error_log /var/log/nginx/opencart_error.log;

    location = /favicon.ico {
      log_not_found off;
      access_log off;
    }
    location = /robots.txt {
      allow all;
      log_not_found off;
      access_log off;
    }
    location / {
      try_files $uri $uri/ /index.php?$args;
    }
    location ~ \.php$ {
      include snippets/fastcgi-php.conf;
      fastcgi_pass unix:/run/php/php7.3-fpm.sock;
    }
    location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg)$ {
      expires max;
      log_not_found off;
    }

  }
```
```
nginx -t
sudo ln -s /etc/nginx/sites-available/opencart.conf /etc/nginx/sites-enabled/
sudo service nginx restart
sudo service php7.3-fpm restart
```
#### postinstall
```
mv /var/www/html/opencart/system/storage/ /var/www/html/storage/
```
#### change /var/www/html/opencart/config.php & admin/config.pgp
- change define('DIR_STORAGE', DIR_SYSTEM . 'storage/'); 
- to define('DIR_STORAGE', '/var/www/html/storage/');

- nano /var/www/html/opencart/admin/model/localisation/currency.php on line 141
- because line: 124 /var/www/html/opencart/admin/model/localisation/currency.php doesnt work anymore

#### [simple module](https://stackoverflow.com/questions/13208488/how-to-make-a-simple-module-in-opencart-example-getting-latest-posts-from-wordp)

#### [create theme](https://www.antropy.co.uk/blog/how-to-create-an-opencart-3-theme/) 
```
  ## bash to create an opencart theme
  cd /var/www/html/opencart
  cd /apps/opencart/htdocs   #googlecloud
  sudo cp -a -r catalog/view/theme/default catalog/view/theme/artheme 

  sudo cp -a admin/language/en-gb/extension/theme/default.php admin/language/en-gb/extension/theme/artheme.php 
  sudo cp -a admin/controller/extension/theme/default.php admin/controller/extension/theme/artheme.php
  sudo cp -a admin/view/template/extension/theme/default.twig admin/view/template/extension/theme/artheme.twig

  sudo sed -i 's/Default Store/Artheme Store/g'  admin/language/en-gb/extension/theme/artheme.php
  sudo sed -i 's/default/artheme/g'  catalog/view/theme/artheme/template/common/header.twig
  sudo sed -i 's/default/artheme/g'  admin/controller/extension/theme/artheme.php
  sudo sed -i 's/ControllerExtensionThemeDefault/ControllerExtensionThemeArtheme/g'  admin/controller/extension/theme/artheme.php
  sudo sed -i 's/theme_default/theme_artheme/g' admin/view/template/extension/theme/artheme.twig
```

- Goto http://localhost/admin 
  >Extension >Extension >Set Filter Themes >Select Action on Artheme >Install
  >System >Settings >Edit >Select Artheme > Save

- Check on chrome devtools if the css points to /catalog/view/theme/artheme/stylesheet/stylesheet.css
- @ /catalog/view/theme/artheme/stylesheet/stylesheet.css add:
```
  .btn-group {
    display:none;
  }
```

- @ catalog/view/theme/artheme/template/common/home.twig change:
```
  sudo sed -i 's/common-home" class="container/common-home" class="container-fluid/g' /catalog/view/theme/artheme/template/common/home.twig
```
- @ catalog/view/theme/artheme/template/common/header.twig  and
- @ catalog/view/theme/artheme/template/common/menu.twig change:
```
  sudo sed -i 's/div class="container/div class="container-fluid/g'  catalog/view/theme/artheme/template/common/header.twig  
  sudo sed -i 's/div class="container/div class="container-fluid/g'  catalog/view/theme/artheme/template/common/menu.twig
```
- @ catalog/view/theme/artheme/template/product/category.twig
```
  sudo grep -rn catalog/view/theme/artheme/template/ -e "product-category"
  sudo sed -i 's/class="container/class="container-fluid/g' catalog/view/theme/artheme/template/product/category.twig
```