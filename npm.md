#### show all globally installed modules
```
	$ npm list -g --depth 0
```
#### show global or local modules folder
```
	$ npm root [-g]
```
#### create package.json on the current folder
```
	$ npm init
```
#### install or uninstall modules globally or locally
```
	$ npm [install|uninstall] [-g] <package>
```
#### install dependency modules & add it to package.json
```
	$ npm install --save <package>
```
#### link a global modules to be used locally for a project
```
	$ npm link <package>
```
#### enable root install without error
```
	$ sudo npm install --unsafe-perm=true -g <package>
```

