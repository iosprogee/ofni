### google app engine 
 [php getting started](https://cloud.google.com/appengine/docs/flexible/php/quickstart)    
 [getting started(php)](https://cloud.google.com/php/getting-started/hello-world)

#### start php gae
```
 $ mkdir <projname>
```  
  - goto [cloud console](https://console.cloud.google.com) 
  - select &lt; projname &gt;
  - click activate cloud shell
  - on cloud shell type  
    ```  
    $ gcloud app create [enter]
    ```  
  - type 1 [enter] for asia-east2(hongkong) region

##### [set the region](https://cloud.google.com/appengine/docs/locations) 

#### deploy (using gcloud)
  ```
  $ gcloud app deploy app.yaml --project=<projname> --version=1
  ```
#### deploy (using appcfg.py) using stored token
  ```
  $ appcfg.py --oauth2_credential_file=~/.appcfg_oauth2_tokens update ../<projectFolder>  
  ```
#### reset token then run appcfg to prompt for credentials
  ```
  $ mv ~/.appcfg_oauth2_tokens appcfg_token_email
  $ appcfg.py update app.yaml .
  ```
#### recover/download gae source
  ```
  $ appcfg.py download_app -A <projectname> <folder>
  $ appcfg.py download_app -A beearvee beearveeBak  --noauth_local_webserver
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

#### php gae
 ```
 composer remove guzzlehttp/guzzle:~6.0
 composer require whatcms/whatcms-php

 gcloud app deploy --project testerific --version 1

 nano app.yaml
 ```  
  ```
  # dev_appserver.py app.yaml
  # gcloud app deploy --project barangay --version 1

  #application: testerific
  #version: 1
  runtime: php55
  api_version: 1
  threadsafe: yes

  handlers:
  - url: /favicon\.ico
    static_files: favicon.ico
    upload: favicon\.ico

  - url: .*
    script: whatcms.php
  ```