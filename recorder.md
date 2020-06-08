### [recorder](https://github.com/ArchangelGabriel/recorder/) 

#### scripts
```
 nano ~/recorder/scripts/consolePanel.ts
```
#### run:
```
 npm run ts-node scripts/consolePanel.ts
```

```

 import { TestService } from "../services/TestService";

 import faker from "faker";
 import snakeCase from "snakecase-keys";
 import { testInstance } from "../modules/bigcommerce";
 import { numberUtils } from "../shared/utils/numberUtils";

 const readline = require("readline");
 const rl = readline.createInterface({
   input: process.stdin,
   output: process.stdout
 });

 type validCmds = "cust" | "order" | "store" |"subs" | "exit"

 (function r(){
   rl.question('Command: ', async (cmd:string) => {
     //console.log(cmd.split(' '));
     let command = cmd.split(' ');
     let arg = command.length>1 ? command[1]:'';
     let fnName = command[0] as validCmds;

     const map = {
       cust,
       order,
       store,
       subs
     }
     if (fnName == 'exit')  return rl.close();
     //if ("cust order store subs exit".includes(command[0])) await window[fnName]();//await map[command](arg);
     await map[fnName]?.(arg);
     r();
   });
 })();

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

```

