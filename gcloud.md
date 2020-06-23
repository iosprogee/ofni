#### install gcloud
```
  $ curl https://sdk.cloud.google.com | bash
  $ cd ~/google-cloud-sdk
  $ ./install.sh
  $ bin/gcloud init
  $ gcloud init --console-only
  $ cd ~
  $ gcloud components install app-engine-php
  $ gcloud components update

```
<!-- 
wget https://dl.google.com/dl/cloudsdk/channels/rapid/google-cloud-sdk.tar.gz
-->
#### install | remove components
```
  $ gcloud components install <COMPONENT_ID>
  $ gcloud components remove <COMPONENT_ID>
```
#### update gcloud
```
  $ gcloud components update
```
#### sample components & id list 
>    |     Status    |                  Name                  |            ID      |    Size  |
>    |     :---      |                 :---                   |           :---     |    ---:  |    
>    | Not Installed | gcloud app PHP Extensions              | app-engine-php     |  21.9 MiB|    
>    | Not Installed | kubectl                                | kubectl            |   < 1 MiB|    
>    | Installed     | BigQuery Command Line Tool             | bq                 |   < 1 MiB|    
>    | Installed     | Cloud SDK Core Libraries               | core               |  10.5 MiB|    
>    | Installed     | Cloud Storage Command Line Tool        | gsutil             |   3.8 MiB|    
  
#### enable spreadsheet api
  - Go to the Google APIs Console.
  - Select or Create a new project.
  - Click Enable API. Search Google Drive API > ENABLE.
  - Create Credentials Google Drive API > Calling API from Web Server
  - Select Application DATA > Select Yes im using one or BOTH
  - Use application Default Credentials [?](https://cloud.google.com/docs/authentication/production?hl=en_US#auth-cloud-implicit-php)
  - Name the service account and grant it a Project Role of Editor.
  - Download the JSON file.
  - Copy the JSON file to your app directory and rename it to client_secret.json
  - composer require google/apiclient:^2.0

[gcloud reference](https://cloud.google.com/sdk/gcloud/reference/compute/ssh)
>> #### notes:    
>> **doesnt work**    
>>    dev_appserver.py --php_executable_path=/usr/bin/php <projectFolder>/


