
#### gcloud opencart (bitnami)
##### [store admin](https://34.87.185.68/admin/index.php?route=common/dashboard)
##### [store front](http://34.87.185.68/index.php?route=common/home)
##### [deployment manager](https://console.cloud.google.com/dm/deployments/details/opencart-1?project=close-cart-280510)
##### [ssh connect to vm instance](https://ssh.cloud.google.com/projects/close-cart-280510/zones/asia-southeast1-a/instances/opencart-1-vm)
```
gcloud auth list
gcloud config set project close-cart-280510
gcloud sql connect closecart --user=root

```
