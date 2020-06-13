> note: 
>  - for dev, use googleAppEngineLauncher & make sure no hash(#) on 'application:' & 'version:' lines
>      'dev_appserver.py app.yaml'  can also be used for dev server
>
>  - for deployment, prefix 'application:' & 'version:' lines with '#'    
>      gcloud app deploy --project barangay --version 1


####  sample app.yaml for php
```
application: barangay
version: 1
runtime: php55
api_version: 1
threadsafe: yes

handlers:
- url: /favicon\.ico
  static_files: favicon.ico
  upload: favicon\.ico

- url: /guzz
  script: guzzleme.php

- url: .*
  script: whatcms.php
```  