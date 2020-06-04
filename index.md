|  <h4>index.md</h4> |
|     :---:     |


#### [code highlighter](https://highlightjs.org/)

<pre> <code>
function bot(){ 
  var x=1;  
  return (x+x) 
}
</code> </pre>

>> #### ruby
>> ```ruby
>> require 'redcarpet'
>> markdown = Redcarpet.new("Hello World!")
>> puts markdown.to_html
>> ```

#### tables

| Left       | Center      | Right         |
| :---       |   :---:     |          ---: |
| 1.         | git status  | git branch -a |
| 2.         | git diff    | git init      |


<table style="width:100%; display: table; border-collapse: collapse; text-align: center;">
  <tr> <td>100</td> </tr>
</table>

#### tasks

- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

#### images

<img src='bot.gif' alt='drawing' width='40'/>

| <span class="material-icons big">keyboard_arrow_right </span> | ![Image](bot.gif) | <span class="material-icons big">keyboard_arrow_left</span> |
| :---    |        :---:        |     ---: |


- Bulleted
- List

1. Numbered
1. List

#### text decor
**Bold**    
_Italic_    
`highlight`


#### references
>> 🔧  [Github Pages Basics](https://help.github.com/categories/github-pages-basics/)   
>> 🛴  [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/)    
>> ❤️  [Emoji CheatSheet](https://gist.github.com/roachhd/1f029bd4b50b8a524f3c)    
>> &#128640;  [Emoji HTML Codes](https://steemit.com/emojis/@blueorgy/steemit-emojis-master-list)    


###### Header 6
##### Header 5
#### Header 4
###  Header 3
##   Header 2
#    Header 1

<script id="jsTAG"  type="text/javascript">
  console.log('changing demo');
  document.getElementById('references').style.color = 'red';
  document.getElementById('references').classList.add('blinker');
  document.getElementById('references').scrollIntoView();
</script>
