#### bigcommerce  
  - [34,876{us}](https://trends.builtwith.com/shop/BigCommerce/United-States)  
  - [22{ph}](https://trends.builtwith.com/websitelist/BigCommerce/Philippines)  

    https://carewell.com  

    https://medicalsuppliesdepot.com.ph  
    https://farmery.ph/  
    https://thepinkshoppe.com/checkout  

    https://japanichi.com.ph/  
    https://freshlypicked.sg/  

  ##### [script manager](https://recorder-sandbox.mybigcommerce.com/manage/script-manager)  
  ```
  //pfont
  <script>
    console.log('pFont');
    document.getElementsByTagName('p').forEach((i)=>{
      if(i.classList=='') i.style.fontSize = "large";
    })
  </script>

  //footCopyHide
  <script>
    document.querySelectorAll('div.footer-copyright').forEach((i)=>{
     i.style.display = "none"; 
    })
  </script>

  //onPrint
 <script>
  var beforePrint = function() {
    document.querySelectorAll('footer.footer').forEach((i)=>{
     i.style.display = "none"; 
    })
    console.log('beforePrinting.');
  };
  var afterPrint = function() {
    document.querySelectorAll('footer.footer').forEach((i)=>{
     i.style.display = "block"; 
    })    
    console.log('afterPrinting');
  };    
  window.onbeforeprint = beforePrint;
  window.onafterprint = afterPrint;
  </script>
  ```
  ##### [storefront > my themes > advance > edit theme files](https://recorder-sandbox.mybigcommerce.com/manage/storefront-manager/my-themes)  
  ```
  //Shows HowTo besides Description tab
  //templates > components > products > description_tabs.html
  //chaange to below:
  <!-- <a class="tab-title" href="#tab-warranty">{{lang 'products.warranty'}}</a>  -->
  <a class="tab-title" href="#tab-warranty">How-To</a>

  ```  

<!--
  ups 1ZR095E40400831514 may25,may27,may29,may30 mitor 
      crown.ph   
      kalmcosmetics.ph
      negosyonow.com
      tatsunoparts.com
      thepinkshoppe.com
      thingsremembered.com.ph
      toykingdom.ph

      iprints.ph  
      downtoearth.ph    
      aquasphereswim.com.ph  
      sakura.ph  
      eazyfashion.com  
      luckydollstore.com  
      danah.ph  

      **sg**
      babyorganix.com.sg    
      store.brewerkz.com   
      bonumlife.com.sg     
      beadsandnails.com    
      buybbcream.com    
      bscoffee.net    
      craftbeer.sg    
      cheeseshop.sg    
      creamhaus.sg    
      creativeideas.com.sg 
      naturaworks.com   
      kiancontract.com.sg 
      tank.com.sg     
      nordicexposure.com.sg 
      thelittlemarket.sg    
      thelearningtee.com    
      thejerseyshop.sg     
      thecostumebase.com    
      tmart.com.sg    
      trinketcove.com
-->

#### opencart  
  - [123{ph}](https://trends.builtwith.com/websitelist/OpenCart/Philippines)  
      shop.globe.com.ph  
      689properties.com.ph  
      f8photo.ph  
      datawelltech.com  
      fashionjewelries.com  
      favori.ph  
      ilovemypets.ph  
      fertilaid.ph  
      aerophone.com.ph  
      babyzone.ph  
      agnus.ph  
      fingertec.ph  
      alatoneplastics.com.ph  
      dfreshly.ph  
  - [developing modules](http://docs.opencart.com/en-gb/developer/module/)    
  - [demo storefront](https://demo.opencart.com/)  
  - [demo admin](https://demo.opencart.com/admin/)  
  - [docker](https://hub.docker.com/r/vimagick/opencart/)  
  - circuit.rocks   


#### shopify   
  - [909,637{us}](https://trends.builtwith.com/shop/Shopify/United-States)  
  - [1,297{ph}](https://trends.builtwith.com/websitelist/Shopify/Philippines)  
      amrag.com  
      mydomesticity.com  
      widgetcity.com.ph  
      complink.com.ph  
      33bigshop.ph  
      booksforless.ph  
      abcshop.ph  
      3dcrystal.ph  
      abundance.ph  
      abubot.ph  
      fabzy.ph  
      daegubeauty.ph  
      ibrowseandbuy.com.ph  
      acmejewelry.com.ph  
      icandypro.ph  
  - [developers](https://shopify.dev/concepts/shopify-introduction)  
  - [devdocs](https://devdocs.prestashop.com/1.7/basics/introduction/)  

#### prestashop  
  - [51{ph}](https://trends.builtwith.com/websitelist/PrestaShop/Philippines)  
<!--  
      farmuraagrivet.ph  
      babyoutlet.ph  
      feral.ph  
      in2it.com.ph  
      instant.com.ph  
      allheadphones.com.ph  
      benstore.com.ph  
      jbsports.com.ph  
      onlinestore.fvp.ph  
      jetclean.com.ph  
-->      
  - [developers](https://www.prestashop.com/en/developers)  
  - [demo](https://demo.prestashop.com/#/en/front)  
  - [docker](https://github.com/yobasystems/alpine-prestashop)  

#### others  
  - magento  
      [bench shop](https://shop.bench.com.ph/)  
  - shopify  
      [penshoppe](https://www.penshoppe.com/)   

#### tools  
  [what cms](https://whatcms.org/?s=www.penshoppe.com)  
  [built with](https://builtwith.com/www.penshoppe.com)  
	[cms detection howto](https://whatcms.org/Content-Management-Systems)  

	[website comprehensive report](https://www.cubdomain.com/site/penshoppe.com)  
  [stat chest](https://www.statchest.com/penshoppe.com.html)  
  [check page rank](https://checkpagerank.net/check-page-rank.php)  

  [way back machine](https://web.archive.org/)  
  [awesome opensource](https://awesomeopensource.com/projects/whois)  


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

