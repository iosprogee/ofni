#### [gdrive](https://github.com/gdrive-org/gdrive) - gdrive cli

#### install
```
 $ go get github.com/prasmussen/gdrive
 $ gdrive bin is  at $GOPATH/bin/gdrive
```
#### list files and folders 
```
 $ gdrive list --query " 'root' in parents"
 $ gdrive list --query " '1xKp1cu7zv7SoZQLj-l_vP-nva0BXajZf' in parents"
```
#### upload info folder recursively to Codes->gaePHP
```
 $ ~/go/bin/gdrive upload -p 1xKp1cu7zv7SoZQLj-l_vP-nva0BXajZf -r info
```
#### make newfolder on MyDrive / Codes->gaePHP
```
 $ ~/go/bin/gdrive mkdir -p root newfolder
 $ ~/go/bin/gdrive mkdir -p 1xKp1cu7zv7SoZQLj-l_vP-nva0BXajZf newfolder
```
#### delete file or folder (recursively)
```
 $ ~/go/bin/gdrive delete -r <fileId>
```
#### gdrives
- [codes > gaePHP](https://drive.google.com/drive/folders/1xKp1cu7zv7SoZQLj-l_vP-nva0BXajZf)
- [INFO](https://drive.google.com/drive/folders/1VkFWrO0NVdq9n0eG2mkutCx_1SHdR5In)