
#### gcloud opencart (bitnami)  
|        |        | 
| :---   |  :---  | 
|   [store admin](https://34.87.185.68/admin/index.php?route=common/dashboard)|   [store front](http://34.87.185.68/index.php?route=common/home) |  
|   [deployment manager](https://console.cloud.google.com/dm/deployments/details/opencart-1?project=close-cart-280510) |   [ssh connect to vm instance](https://ssh.cloud.google.com/projects/close-cart-280510/zones/asia-southeast1-a/instances/opencart-1-vm) |   

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

#### [phpadmin via sshtunnel](https://docs.bitnami.com/aws/faq/get-started/access-phpmyadmin/#access-phpmyadmin-on-linux-and-macos)
```
gcloud auth list
gcloud config set project close-cart-280510
gcloud sql connect closecart --user=root
```

#### [apache conf](https://docs.bitnami.com/installer/apps/opencart/get-started/understand-config/)
#### [enable modules](https://docs.bitnami.com/bch/apps/opencart/configuration/enable-modules/)
```
sudo /opt/bitnami/ctlscript.sh restart apache

nano /opt/bitnami/apache2/conf/httpd.conf

cat /opt/bitnami/apache2/conf/httpd.conf | grep "Server"
  ServerRoot "/opt/bitnami/apache2"

cat /opt/bitnami/apache2/conf/httpd.conf | grep "Document"

sudo grep -rnw /opt/bitnami/apache2/conf/ -e "opencart"
  /opt/bitnami/apache2/conf/bitnami/bitnami-apps-prefix.conf:2:Include "/opt/bitnami/apps/opencart/conf/httpd-prefix.conf"
```

#### [connect to gcloud ssh](https://cloud.google.com/compute/docs/instances/connecting-advanced#provide-key)
#### [add ssh keys](https://cloud.google.com/compute/docs/instances/managing-instance-access#add_oslogin_keys)
```
gcloud compute os-login ssh-keys add --key-file key-file-path  --ttl expire-time
```    