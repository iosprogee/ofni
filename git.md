
#### start gh-pages 
```
  echo "# dplyme.github.io" >> README.md
  git init
  git add README.md
  git commit -m "1st"
  git remote add origin https://github.com/<username>/<repo>.git
  git push origin master
```
### repl 
```bash
  $ git add .
  $ git commit -m "2nd commit"
  $ git push origin master
```
---

#### UPDATE <username>.github.io
``` 
  git add -A             #--all
  git commit -m 'all'
  #git remote add origin https://github.com/<username>/<username>.github.io
  git remote add origin https://github.com/iosprogee/ofni
  git push origin master # popup deny 
```
#### configure name, email
```
  git config --global user.email "name@gmail.com"
  git config --global user.name "name"
  git config --global --list
```
#### ⛑️ git config file 
```
  [cat|nano] .git/config 
```
#### gh-pages to master 
```
  git checkout gh-pages
  git merge master
  git push origin gh-pages
```
#### gh-pages to new repo
```
  git init
  git add README.md
  git commit -m "1st commit"
  git add remote origin url https://github.com/<username>/<username>.github.io.git
  git push -u origin master
```

> | references |           |
> |   :---     |     ---: |
> | [Github Pages](https://pages.github.com/) | <span class="material-icons">keyboard_arrow_left</span> |
> | [Emoji HTML Codes](https://steemit.com/emojis/@blueorgy/steemit-emojis-master-list) | <span class="material-icons">keyboard_arrow_left</span> |

