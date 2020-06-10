### google app engine 
 [php getting started](https://cloud.google.com/appengine/docs/flexible/php/quickstart)    
 [getting started(php)](https://cloud.google.com/php/getting-started/hello-world)

#### start php gae
```
 $ mkdir <projname>
```  
  - goto [cloud console](https://console.cloud.google.com) 
  - select <projname>
  - click activate cloud shell
  - on cloud shell type  
    ```  
    $gcloud app create [enter]
    ```  
  - type 1 [enter] for asia-east2(hongkong) region

##### [set the region](https://cloud.google.com/appengine/docs/locations) 

#### deploy (using gcloud)
  ```
  $ gcloud app deploy app.yaml --project=<projname> --version=1
  ```
#### run dev server
  ```
  $ dev_appserver.py ../k1mathadd  _[OR]_   
  $ php -S localhost:8080 -t web/
  ```
#### optionally set default project 
  ```
  $ gcloud config set project k1mathadd
  ```
#### cli
  ```
  $ gcloud auth list
  $ gcloud config list
  $ gcloud info
  $ gcloud config set account <io...@gmail>
  $ gcloud auth login
  $ gcloud projects list
  ```
#### recover gae source
  ```
  $ appcfg.py download_app -A <projectname> <folder>
  $ appcfg.py download_app -A beearvee beearveeBak
  ```

