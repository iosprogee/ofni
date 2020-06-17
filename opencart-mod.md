#### [develop modules](http://docs.opencart.com/en-gb/developer/module/)

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

 sudo sed -i 's/#303030/rgba(19,32,58,1)/g' catalog/view/theme/artheme/stylesheet/stylesheet.css
 sudo sed -i 's/#229ac8/rgba(58,88,173,1)/g' catalog/view/theme/artheme/stylesheet/stylesheet.css
<!--
background-image: linear-gradient(to bottom, #23a1d1, #1f90bb);
background-repeat: repeat-x;
border-color: #1f90bb #1f90bb #145e7a;
-->

#### remove Powered by
```
sudo grep -rn catalog/language/  -e "powered"
catalog/language/en-gb/common/footer.php:17:$_['text_powered'] = 'Powered By <a href="http://www.opencart.com">OpenCart</a><br /> %s &copy; %s';

sudo nano catalog/view/theme/artheme/template/common/footer.twig

sudo grep -rn catalog -e "bitnami-banner"
```

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

