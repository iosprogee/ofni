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

