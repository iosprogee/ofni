#### [termux go](https://teachwithf.blogspot.com/2018/12/golang-install-in-android-using-termux.html)
```
  $ pkg install golang
```

#### [osx go](https://www.digitalocean.com/community/tutorials/how-to-install-go-and-set-up-a-local-programming-environment-on-macos)
```
 brew doctor
 brew install golang
 brew upgrade golang
 mkdir -p $HOME/go/{bin,src}
```
```
 nano ~/.profile
```
> ```
> export GOPATH=$HOME/go
> export PATH=$PATH:$GOPATH/bin
> ```

#### get src from github
```
 go get github.com/digitalocean/godo
 ls -lh src/github.com/digitalocean/godo/
```
#### run
```
 go run hello.go
```
#### compile to bin 
```
 go build hello.go
 go install <package>
```
