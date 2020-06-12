##### [script manager](https://recorder-sandbox.mybigcommerce.com/manage/script-manager)  

#### [embed handlebars](https://developer.bigcommerce.com/stencil-docs/reference-docs/handlebars-helpers-reference)
```
<script>
console.log('prod id: {{product.id}}');
</script>
```
#### call to action   
```
<script id="popperoo" type="text/html">
<div id="popperoo-div" style="display:none;position:fixed;top:0;left:0;width:100%;height:100%;z-index:1000;" >
  <div class="graybak" style="width:100%;height:100%;position:absolute;top:0;left:0;background-color:rgba(0,0,0,.5);cursor:pointer;-webkit-animation:fadein .5s;animation:fadein .5s;"></div>
  <div class="mdl" style="width:600px;height:400px;background-color:#f0f1f2;z-index:1;position:absolute;margin:auto;top:0;right:0;bottom:0;left:0;border-radius:4px;-webkit-animation:popin .3s;animation:popin .3s;">
    <div class="mdl-title" style="font-size:18px;background-color:#0082D3;color:#fff;padding:10px;margin:0;border-radius:4px 4px 0 0;text-align:center;">
      <h3 style="color:#fff;font-size:1em;margin:.2em;text-transform:uppercase;font-weight:500
">It's On Us</h3>
    </div>
    <div class="mdl-body" style="padding:20px 35px;font-size:.9em;">
      <p>Thanks for stoping by!</p>
      <br>
      <p style="color:#344a5f;line-height:1.3em;">A demo dialog where you can include buttons, capture email or display messages for your audience. Anything is possible. The sky's the limit!</p>
      <br>
      <p style="color:#344a5f;line-height:1.3em;">Close it  by clicking "No Thanks" or you could also click anywhere outside.</p>

      <form style="text-align:center;margin-top:35px">
        <input type="text" placeholder="you@email.com" style="padding:12px;font-size:1.2em;width:300px;border-radius:4px;border:1px solid #ccc;-webkit-font-smoothing:antialiased">
        <input type="submit" value="learn more »" style="text-transform:uppercase;font-weight:700;padding:12px;font-size:1.1em;border-radius:4px;color:#fff;background-color:#4ab471;border:none;cursor:pointer;-webkit-font-smoothing:antialiased">
        <p class="form-notice" style="text-align:left;margin-left:40px;opacity:.8;margin-top:1px;padding-top:1px;font-size:.9em
">*confidential</p>
      </form>
    </div>
    <div class="mdl-footer" style="position:absolute;bottom:20px;text-align:center;width:100%">
      <p style="text-transform:capitalize;cursor:pointer;display:inline;border-bottom:1px solid #344a5f
">no thanks</p>
    </div>
  </div>
</div>
</script>
<script>
!function(e,i){"function"==typeof define&&define.amd?define(i):"object"==typeof exports?module.exports=i(require,exports,module):e.ouibounce=i()}(this,function(){return function(e,i){function n(e,i){return"undefined"==typeof e?i:e}function o(e){var i=24*e*60*60*1e3,n=new Date;return n.setTime(n.getTime()+i),"; expires="+n.toGMTString()}function t(){y.addEventListener("mouseleave",u),y.addEventListener("keydown",r)}function u(e){e.clientY>s||c("viewedOuibounceModal","true")&&!f||(d(),v())}function r(e){b||c("viewedOuibounceModal","true")&&!f||e.metaKey&&76==e.keyCode&&(b=!0,d(),v())}function c(e,i){var n=document.cookie.split("; ").reduce(function(e,i){var n=i.split("=");return e[n[0]]=n[1],e},{});return n[e]===i}function d(){e&&(e.style.display="block"),a()}function a(e){var e=e||{};"undefined"!=typeof e.cookieExpire&&(l=o(e.cookieExpire)),e.sitewide===!0&&(k=";path=/"),"undefined"!=typeof e.cookieDomain&&(p=";domain="+e.cookieDomain),document.cookie="viewedOuibounceModal=true"+l+p+k,y.removeEventListener("mouseleave",u),y.removeEventListener("keydown",r)}var i=i||{},f=i.aggressive||!1,s=n(i.sensitivity,20),m=n(i.timer,1e3),v=i.callback||function(){},l=o(i.cookieExpire)||"",p=i.cookieDomain?";domain="+i.cookieDomain:"",k=i.sitewide===!0?";path=/":"",y=document.getElementsByTagName("html")[0];setTimeout(t,m);var b=!1;return{fire:d,disable:a}}});
document.querySelectorAll('header.header').forEach((i)=>{
 //i.style.height = "50px"; 
})
  document.body.innerHTML += document.getElementById('popperoo').innerHTML;
    
var _ouibounce = ouibounce(document.getElementById('popperoo-div'), {
  aggressive: true,
  timer: 0,
  callback: function() { console.log('popperoo fired!'); }
});
document.addEventListener('click', function(event) {
  document.getElementById('popperoo-div').style.display="none";
});    
    
  console.clear();console.log("popperoo");
</script>
```
