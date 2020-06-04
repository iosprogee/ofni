#### [nmap usage](https://www.digitalocean.com/community/tutorials/how-to-use-nmap-to-scan-for-open-ports-on-your-vps)

#### install (osx)
```
  $ brew install nmap
  $ nmap -V
```

#### usage
```
  $ sudo nmap -sS -p 22 192.168.1.0/24
  $ sudo nmap -p 22 --open -sV 192.168.1.0/24
```  