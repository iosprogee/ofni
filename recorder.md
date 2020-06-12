### [recorder](https://github.com/ArchangelGabriel/recorder/) 

#### scripts
```
 nano ~/recorder/scripts/consolePanel.ts
```

```
/*
file:
  scripts > test.ts
run:
  npm run ts-node scripts/consolePanel.ts
update:
  git pull origin gabe/bigcommerce-script  
*/
import { TestService } from "../services/TestService";

import faker from "faker";
import snakeCase from "snakecase-keys";
import { testInstance } from "../modules/bigcommerce";
import { numberUtils } from "../shared/utils/numberUtils";

/*getConsoleInput*/
const readline = require("readline");
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});
type validCmds = "cust"|"order"|"store"|"subs"|"fake"|"script"|"exit"

(function r(){
  rl.question('Command: ', async (cmd:string) => {
    //console.log(cmd.split(' '));
    var command = cmd.split(' ');
    let arg = command.length > 1 ? command[1]:'';
    let fnName = command[0] as validCmds;

    const map = { cust, order, store, subs, fake, script}

    if (fnName == 'exit')  return rl.close();
    //if ("cust order store subs exit".includes(command[0])) await window[fnName]();//await map[command](arg);
    arg = command.length > 2 ? cmd : command[1];
    await map[fnName]?.(arg);
    if(typeof map[fnName] === 'undefined' ) console.log('invalid command!');
    r();
  });
})();
/*eo getConsoleInput*/

/*
  script commands:
  script del 4d31cd85-beae-466a-b46a-6688bf823b44
  script make galingmo console.log('galingko');
  script make bchook https://iosprogee.github.io/ofni/bchook.js
  script make testerific https://testerific.appspot.com/i.js?t=hash_token
*/
async function script(arg:string='') {
  const ts = await TestService.getInstance();
  const scripts = await ts.bigcommerceScriptModule.list();
  arg = arg.trim();
  //command = arg.includes(' ') ? : arg.split(' '): command;

  if( arg!='' && "0123456789".includes(arg) )
    { console.log('query:'); console.log(scripts[Number(`${arg}`)]) }
  else if(arg.includes('make'))
    await scriptCreate(arg.split(' ')[2],arg.split(' ')[3]);
  else if( arg.includes('del') ){
      console.log(`deleting: ${arg.split(' ')[2]}`);  
      await ts.bigcommerceScriptModule.remove(arg.split(' ')[2]); }
  else 
    { console.log('all:'); console.log(scripts); }
}

type validKinds = "src" | "script_tag"
async function scriptCreate(name:string='Scripter', html:string="console.log('scripter')" ) {
  const ts = await TestService.getInstance();
  const store = await ts.storeService.get(ts.storeId);
  var href = '';
  let kindred = "script_tag" as validKinds ;

  console.log(`Creating Script ${name}...`);
  if (html.includes("http")){
    kindred = "src";
    href = html;
    html = '';
  } else{
    html = "<script>" + html + "</script>"
  }
  console.log(`src: ${href}`);
  
  try {
    await ts.bigcommerceScriptModule.create({
      name: name,
      description: "Script created programatically",
      kind: kindred,
      html: html,
      src: href,
      autoUninstall: false,
      loadMethod: "default",
      location: "footer",
      visibility: "all_pages",
      consentCategory: "essential",
    });
  } catch (err) {
    console.error(err.response.data);
  }
  console.log("Done!!!");
}

async function cust(arg:string='') {
  const ts = await TestService.getInstance();
  //found in: modules > bigcommerce > customer.ts
  const customers = await ts.bigcommerceCustomerModule.list(); 
  if(arg == 'len')  
    console.log(customers.length)
  else 
    console.log(customers[0]);
}

async function order(arg:string='') {
  const ts = await TestService.getInstance();
  const orders = await ts.bigcommerceOrderModule.list();
  console.log(orders[0]);
}

async function store(arg:string='') {
  const ts = await TestService.getInstance();
  const store= await ts.storeService.get(ts.storeId);
  console.log(store.scope.split(' '));
}

async function subs(arg:string='') {
  const ts = await TestService.getInstance();
  //found in: services > SubscriptionService.ts
  const subs = await ts.subscriptionService.list(); 
  if(arg == 'len')  
    console.log(subs.length)
  else 
    console.log(subs[0]);
}

/*productGenerator*/
async function fakeMe(arg:string='') {
  var item = await generateProduct()
  console.log(item);
}

async function fake(arg:string='') {
  await testInstance()
    .post("/v3/catalog/products", generateProduct())
    .then((item) => console.log(item))
    .catch((err) => console.error(err.response.data));
}

const generateProduct = () => {
  const images = numberUtils.getVariableSizeArr(1, 3).map(() => ({
    imageUrl:
      "https://loremflickr.com/320/240?lock=" + faker.random.number(1084),
  }));

  const variants = numberUtils.getVariableSizeArr(1, 3).map(() => {
    const label = faker.random.word();
    return {
      sku: faker.random.word(),
      optionValues: numberUtils.getVariableSizeArr(1, 3).map(() => ({
        label,
        optionDisplayName: faker.random.word(),
      })),
    };
  });

  return snakeCase(
    {
      name: faker.random.words(2),
      price: faker.random.number(999),
      type: "physical",
      categories: [23],
      variants,
      images,
      weight: 0,
    },
    { deep: true },
  );
};
/*eo productGenerator*/

```

#### run:
```
 npm run ts-node scripts/consolePanel.ts
```

#### splash page before user leaves   
```

<script id="popModal" type="text/html">
<div id="pop-mdl" style="display:none;position:fixed;top:0;left:0;width:100%;height:100%;z-index:1000;" >
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
  document.body.innerHTML += document.getElementById('popModal').innerHTML;
    
var _ouibounce = ouibounce(document.getElementById('pop-mdl'), {
  aggressive: true,
  timer: 0,
  callback: function() { console.log('ouibounce fired!'); }
});
document.addEventListener('click', function(event) {
  document.getElementById('pop-mdl').style.display="none";
});    
    
  console.clear();console.log("popperoo");
</script>
```

