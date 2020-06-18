#### [develop modules](http://docs.opencart.com/en-gb/developer/module/)
#### [optimize code](https://webkul.com/blog/optimize-your-opencart-code/)

#### enable SEO URLs 
- goto Admin Page -> System -> Settings  
- click on "Edit"  
- click on “Server” tab  
- scroll to “Use SEO URL’s”  
- tick on “Yes”   
- click on "Save" 

#### [create theme](https://www.antropy.co.uk/blog/how-to-create-an-opencart-3-theme/) 
```
  ## bash to create an opencart theme
  cd /var/www/html/opencart
  cd /apps/opencart/htdocs   #googlecloud
  sudo cp -a -r catalog/view/theme/default catalog/view/theme/artheme 

  sudo cp -a admin/language/en-gb/extension/theme/default.php admin/language/en-gb/extension/theme/artheme.php 
  sudo cp -a admin/controller/extension/theme/default.php admin/controller/extension/theme/artheme.php
  sudo cp -a admin/view/template/extension/theme/default.twig admin/view/template/extension/theme/artheme.twig

  sudo sed -i 's/Default Store/Artheme Store/g'  admin/language/en-gb/extension/theme/artheme.php
  sudo sed -i 's/default/artheme/g'  catalog/view/theme/artheme/template/common/header.twig
  sudo sed -i 's/default/artheme/g'  admin/controller/extension/theme/artheme.php
  sudo sed -i 's/ControllerExtensionThemeDefault/ControllerExtensionThemeArtheme/g'  admin/controller/extension/theme/artheme.php
  sudo sed -i 's/theme_default/theme_artheme/g' admin/view/template/extension/theme/artheme.twig
```

- goto http://localhost/admin
```
  >Extension >Extension >Set Filter Themes >Select Action on Artheme >Install   
  >System >Settings >Edit >Select Artheme > Save
```
- Check on chrome devtools if the css points to /catalog/view/theme/artheme/stylesheet/stylesheet.css
- @ catalog/view/theme/artheme/stylesheet/stylesheet.css add:
```
  .btn-group {
    display:none;
  }
```

- @ catalog/view/theme/artheme/template/common/home.twig change:
```
  sudo sed -i 's/common-home" class="container/common-home" class="container-fluid/g' /catalog/view/theme/artheme/template/common/home.twig
```
- @ catalog/view/theme/artheme/template/common/header.twig  and
- @ catalog/view/theme/artheme/template/common/menu.twig change:
```
  sudo sed -i 's/div class="container/div class="container-fluid/g'  catalog/view/theme/artheme/template/common/header.twig  
  sudo sed -i 's/div class="container/div class="container-fluid/g'  catalog/view/theme/artheme/template/common/menu.twig
```
- @ catalog/view/theme/artheme/template/product/category.twig
```
  sudo grep -rn catalog/view/theme/artheme/template/ -e "product-category"
  sudo sed -i 's/class="container/class="container-fluid/g' catalog/view/theme/artheme/template/product/category.twig
```
 ## color change
 sudo sed -i 's/#303030/rgba(19,32,58,1)/g' catalog/view/theme/artheme/stylesheet/stylesheet.css
 sudo sed -i 's/#229ac8/rgba(58,88,173,1)/g' catalog/view/theme/artheme/stylesheet/stylesheet.css

 sudo sed -i 's/#23a1d1/#1565c0/g' catalog/view/theme/artheme/stylesheet/stylesheet.css
 sudo sed -i 's/#1f90bb/#0d47a1/g' catalog/view/theme/artheme/stylesheet/stylesheet.css
 sudo sed -i 's/#333/#455a64/g' catalog/view/theme/artheme/stylesheet/stylesheet.css
 sudo sed -i 's/#666/#37474f/g' catalog/view/theme/artheme/stylesheet/stylesheet.css

 sudo sed -i 's/#EEEEEE/#37568c/g' catalog/view/theme/artheme/stylesheet/stylesheet.css
    border-bottom: 1px solid #e2e2e2;

 ## top-links a
 sudo sed -i 's/color: #888/color: #F8F8F8/g' catalog/view/theme/artheme/stylesheet/stylesheet.css
 sudo sed -i 's/text-shadow: 0 1px 0 #FFF;/text-shadow: 0 1px 0 #A8A8A8/g' catalog/view/theme/artheme/stylesheet/stylesheet.css


 ## button-group
 sudo sed -i 's/border-top: 1px solid #ddd/border-top: 1px solid #27467c/g' catalog/view/theme/artheme/stylesheet/stylesheet.css
 sudo sed -i 's/background-color: #eee/background-color: #37568c/g' catalog/view/theme/artheme/stylesheet/stylesheet.css

    
<!--
background-image: linear-gradient(to bottom, #23a1d1, #1f90bb);
background-repeat: repeat-x;
border-color: #1f90bb #1f90bb #145e7a;
-->

#### remove Bitnami banner
```
## disable banner
  sudo touch /opt/bitnami/apps/bitnami/banner/disable-banner

##discover where banner is
  grep -rn apps/opencart/ -e "bitnami"
  cat /opt/bitnami/apps/bitnami/banner/conf/banner-substitutions.conf

## does not work even if script was replaced
  sudo sed -i 's#<script type="text/javascript" src="/bitnami/banner.js">#<script>#g' /opt/bitnami/apps/bitnami/banner/conf/banner-substitutions.conf
```

#### remove Powered by
```
## replace text_powered
sudo sed -i "s#\$\_\['text_powered'\]#\$\_\['text_powered'\] = ''; //#g" catalog/language/en-gb/common/footer.php

## discover where power is
grep -n catalog/language/en-gb/common/footer.php -e "powered"
catalog/language/en-gb/common/footer.php:17:$_['text_powered'] = 'Powered By <a href="http://www.opencart.com">OpenCart</a><br /> %s &copy; %s';
## check sed is working
sed "s#\$\_\['text_powered'\]#\$\_\['text_powered'\] = ''; //#g" catalog/language/en-gb/common/footer.php > ~/temp
sed '17q;d' ~/temp

```
#### [regex tester](https://www.regexpal.com/27540)


#### [starter module](https://github.com/settysantu/starter-module)

#### [simple module](https://stackoverflow.com/questions/13208488/how-to-make-a-simple-module-in-opencart-example-getting-latest-posts-from-wordp)
 - `sudo nano catalog/view/theme/artheme/template/common/home.twig`
 ```
 <!-- WORKS -->
 #add @ end of home.twig
 <script>console.log('home.twig')</script>
 ```
 -  doesnt work!! add  `<?php arteeModMe() ?>` after `<h1 style="display: none;"><?php echo $heading_title; ?></h1>`
 - `sudo nano catalog/controller/common/home.php`
```
<!-- NOT WORKING -->
#add @ end of home.php

function arteeModMe(){
  //$sql=mysql_query("SELECT * FROM `wordpress_db`.`wp_posts` ORDER BY `wp_posts`.`post_date` DESC LIMIT 5");
  $sql=array()

  //while($row = mysql_fetch_array($sql)){
    $id    = '123';//$row["ID"];
    $author= 'robert smith';//$row["post_author"];
    $date  = '10/20/2020';//$row["post_date"];
    $post  = 'this is a sample content';//$row["post_content"];
    $title = 'a sample title';//$row["post_title"];
    echo '
      <div id="postID_'.$id.'>
        <h3>'.$title.'</h3>
        <p>'.$post.'</p>
        <p>Posted by '.$author.' on '.$date.'</p>
      </div>
    ';

  //}
}
```

