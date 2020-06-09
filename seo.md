#### [back link checker](https://ahrefs.com/backlink-checker)
#### [cms detector](https://whatcms.org/?s=)
#### [built with](https://builtwith.com/www.penshoppe.com)
#### [woo rank](https://www.woorank.com/en/www/circuit.rocks)
#### [site audit](https://app.neilpatel.com/en/seo_analyzer/site_audit?domain=circuit.rocks&submit=Analyze+Website)
#### [website comprehensive report](https://www.cubdomain.com/site/penshoppe.com)  

#### recon
```
#!/bin/bash

clear

CURL_TIMEOUT=15 
CURL_UA=Mozilla 

TARGET=$1
TARGET=ichoose.ph

EXTERNAL_IP=$(curl -A $CURL_UA --silent --connect-timeout $CURL_TIMEOUT http://ipinfo.io/ip)
GEOIP=$(curl -A $CURL_UA --silent --connect-timeout $CURL_TIMEOUT http://ip-api.com/csv/$EXTERNAL_IP)
TARGET_IP=$(echo $GEOIP | cut -d',' -f1 | cut -d '"' -f2)

TARGET_HOST=$(echo $TARGET | cut -d'/' -f3 | cut -d':' -f1)
TARGET=$(curl --fail -A $CURL_UA -L --write-out "%{url_effective}\n" --silent --connect-timeout $CURL_TIMEOUT --output /dev/null $1)

GEOIP=$(curl -A $CURL_UA --silent --connect-timeout $CURL_TIMEOUT http://ip-api.com/csv/$TARGET_HOST)
LOG_IP=`cat log.csv | cut -d',' -f2 | grep $TARGET_IP | wc -l | sed -e 's/^[ \t]*//'`


/* start here */
TARGET=$(curl --fail -A $CURL_UA -L --write-out "%{url_effective}\n" --silent --connect-timeout $CURL_TIMEOUT --output /dev/null ichoose.ph)
TARGET_HOST=$(echo $TARGET | cut -d'/' -f3 | cut -d':' -f1)
GEOIP=$(curl -A $CURL_UA --silent --connect-timeout $CURL_TIMEOUT http://ip-api.com/csv/$TARGET_HOST)
TARGET_IP=$(echo $GEOIP | cut -d',' -f1 | cut -d '"' -f2)
TARGET_IP=$(echo $GEOIP | cut -d',' -f15)

echo [INFO] ------TARGET info------
echo [*] TARGET: $TARGET

TARGET_DNS=$(dig -t SOA $TARGET_HOST | grep -A1 "AUTHORITY SECTION\|ANSWER SECTION" | awk '{print$5}' | sed '/^$/d') &&echo [*] DNS servers: ${TARGET_DNS[@]}
TARGET_SERVER=$(curl -A $CURL_UA -I -L --silent http://$TARGET_HOST/ | grep Server: | uniq | cut -d' ' -f2-10) && echo [*] TARGET server: $TARGET_SERVER
TARGET_IP_CC=$(echo $GEOIP | cut -d',' -f3 | cut -d '"' -f2) && echo [*] CC: $TARGET_IP_CC
TARGET_IP_CN=$(echo $GEOIP | cut -d',' -f2 | cut -d '"' -f2) && echo [*] Country: $TARGET_IP_CN
TARGET_IP_CITY=$(echo $GEOIP | cut -d',' -f6 | cut -d '"' -f2) && echo [*] City: $TARGET_IP_CITY

WHOIS_IP=`whois -h riswhois.ripe.net $TARGET_IP | egrep "route|origin|descr" | head -4`
TARGET_IP_ASN=$(echo $WHOIS_IP | awk '{print$13}') && echo [*] ASN: $TARGET_IP_ASN
TARGET_IP_BGP=$(echo $WHOIS_IP | awk '{print$11}') && echo [*] BGP_PREFIX: $TARGET_IP_BGP
TARGET_IP_ISP=$(echo $WHOIS_IP | cut -d' ' -f15-28) && echo [*] ISP: $TARGET_IP_ISP

if [[ $TARGET =~ ^https ]]; then
  echo "[INFO] SSL/HTTPS certificate detected"
  SSL_ISSUER=`echo | openssl s_client -servername $TARGET_HOST -connect $TARGET_HOST:443 2>/dev/null | openssl x509 -noout -issuer -subject | grep "issuer"` && echo [*] Issuer: $SSL_ISSUER
  SSL_SUBJECT=`echo | openssl s_client -servername $TARGET_HOST -connect $TARGET_HOST:443 2>/dev/null | openssl x509 -noout -issuer -subject | grep "subject"` && echo [*] Subject: $SSL_SUBJECT
  SSL_ISSUER_LETS=`echo $SSL_ISSUER | grep -oiE "let.?s.?encrypt"`
    if [[ $SSL_ISSUER_LETS != "" ]]; then
    echo "[ALERT] Let's Encrypt is commonly used for Phishing"
    fi
  fi
fi

```

