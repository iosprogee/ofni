
#### modules for react gh-pages
```
  $ npm i -g gh-pages
  $ npm i -g create-react-app
```
#### start a react app
```
  $ npx create-react-app <projname> 
  $ cd <projname>
```
#### setup package.json
```
  $ nano package.json
``` 
> ```
>  "homepage": "https://iosprogee.github.io/<projname>",
>  "scripts": {
>    "deploy": "gh-pages -d build",
>    "build": "GENERATE_SOURCEMAP=false react-scripts build",
>  },
> ```
#### initialize git (one time only)
```
  $ git init
  $ git config user.email iosprogee@gmail.com
  $ git config remote.origin.url https://github.com/iosprogee/dplyme.git
```
#### deploy (on every coderefactor)
```
  $ npm run build
  $ npm run deploy
```
#### REPL
```bash
  $ npm install
  $ npm run build
  $ npm start
```
#### install material-ui  & firebase
```
  $ npm install @material-ui/core
  $ npm install @material-ui/icons
  $ npm install --save firebase
  
  #npm install --save react-router-dom
```
##### get firebaseConfig
  - [goto firebase settings](https://console.firebase.google.com/project/fireupmyapp/settings/general/)
  - scroll down to firebase sdk snippet 
  - tick on config 
  - copy the settings

> ```javascript
>   const firebaseConfig = {
>     apiKey: "AIzaSyDMSdTQr8Y-FZWMgFMvb3tDyRf_y44KYis",
>     authDomain: "fireupmyapp.firebaseapp.com",
>     databaseURL: "https://fireupmyapp.firebaseio.com",
>     projectId: "fireupmyapp",
>     storageBucket: "fireupmyapp.appspot.com",
>     messagingSenderId: "823746792317",
>     appId: "1:823746792317:web:efbf29d7dc522a5a329a14",
>     measurementId: "G-M08RXEKFFQ"
>   };
> ```
>
> **save to src/firebase/firebase.js**
#### references
[react getting started](https://create-react-app.dev/docs/getting-started)    
[react firebase](https://itnext.io/firebase-login-functionality-from-scratch-with-react-redux-2bf316e5820f)    
[firebase login](https://github.com/chaseoc/firebase-login-page)    
