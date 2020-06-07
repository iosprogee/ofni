#### [termux](https://medium.com/alize-in-cryptoland/how-to-run-a-secure-chat-behind-tor-off-of-your-android-phone-be83a678693d
)   
```
  $ pkg upgrade && pkg install -y nano git nodejs tor torsocks curl
  $ ip a | grep 192  
  $ nano $PREFIX/etc/tor/torrc  
```
```
    HiddenServiceDir /data/data/com.termux/files/usr/local/var/lib/tor/hidden_service/
    HiddenServicePort 3000 127.0.0.1:80
```
```
  # mkdir if forlder doesnt exist
  $ mkdir -p $PREFIX/usr/local/var/lib/tor/hidden_service   

  # start tor & get onion adrs
  $ tor
  $ cat $PREFIX/usr/local/var/lib/tor/hidden_service/hostname

```

#### [osx](https://tor.stackexchange.com/questions/20231/new-to-tor-is-not-working)
```
  $ brew install tor polipo privoxy  
  $ nano /usr/local/etc/polipo/config  
```
> ```
>   socksParentProxy = "localhost:9050"
>   socksProxyType = socks5
> ```

```
  nano /usr/local/etc/privoxy/config
``
> **uncomment below line**
> ```
>   forward-socks5t / 127.0.0.1:9050 .
> ```

#### start(run & start @boot) or run(one time only) the services
```
  $ brew services [start|run] tor  
  $ brew services [start|run] polipo  
  $ brew services [start|run] privoxy  
```    

#### unix default Tor port (9050)
```
  $ curl --socks5-hostname localhost:9050 https://check.torproject.org  
  $ tail -f /usr/local/var/log/tor.log  
```

