
#### install
```
  brew install tor polipo privoxy
````
#### configure: [ref](https://tor.stackexchange.com/questions/20231/new-to-tor-is-not-working)
```
  nano /usr/local/etc/polipo/config
```
> ```
>    socksParentProxy = "localhost:9050"
>    socksProxyType = socks5
> ```

```
  nano /usr/local/etc/privoxy/config
```
> **uncomment below line**
> ```
>    forward-socks5t / 127.0.0.1:9050 .
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
```

tail -f /usr/local/var/log/tor.log  