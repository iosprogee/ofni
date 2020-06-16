
#### gcloud mysql
##### [instance closecart](https://console.cloud.google.com/sql/create-instance-mysql?project=close-cart-280510)
##### [quickstart guide](https://cloud.google.com/sql/docs/mysql/quickstart)
##### [connect external app](https://cloud.google.com/sql/docs/mysql/connect-external-app)
<!-- root Z..9 -->

```
gcloud auth list
gcloud config set project close-cart-280510
gcloud sql connect closecart --user=root

```

<!--
  bitnami opencart-1 deployment (admin/opencart1103)
  https://console.cloud.google.com/dm/deployments/details/opencart-1?project=close-cart-280510

  VM
  https://console.cloud.google.com/compute/instancesDetail/zones/asia-southeast1-a/instances/opencart-1-vm

  /opt/bitnami/mysql/bin/mysqladmin -p -u root password NEW_PASSWORD

  mysql -u root -p (v3xwrXyCCtwn)
  > ALTER USER 'root'@'localhost' IDENTIFIED BY 'z..9';
  > UPDATE mysql.user SET Password=PASSWORD('z..9') WHERE User='root';
  > FLUSH PRIVILEGES;

## notes:
admin/model/user/user.php line 13
select password from oc_user where user_id=1;
select sha1(concat(`salt`,sha1(concat(`salt`,sha1('v3xwrXyCCtwn'))))) from oc_user where user_id=1;

### change opencart admin password 
update `oc_user` set `password` = sha1( concat(`salt`, sha1( concat(`salt`, sha1('opencart1103'))))) where user_id = 1

### ssh to VM
cd /apps/opencart/htdocs

grep btn-grp catalog/view/theme/default/template/common/home.twig
-->
