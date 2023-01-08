# Wordpress CheatSheet - မြန်မာ version
-------
### Theme creation
theme create လုပ်မယ်ဆို

အရင်ဆုံး 
wp-content/themes ဆိုတဲ့ folder ထဲမှာမှာ
ကိုယ်ရဲ့ ကိုယ်ပိုင် theme folder တစ်ခုဆောက်ပါ

ပြီးတော့ အဓိက ပါရမယ့်  file ၃ ခု
```plaintext
index.php  
screenshot.png // size က 1200 px X 900 px ရှိရမယ်
style.css <=== style ထဲမှာ Theme နာမည်တွေ info တွေ ထည့်ရမယ်
```
style.css ထိပ်ဆုံးမှာထည့်ရတဲ့ comment ဥပမာ

```css
/*
Theme Name: Twenty Twenty
Text Domain: twentytwenty
Version: 1.1
Requires at least: 4.7
Requires PHP: 5.2.4
Description: Our default theme for 2020 is designed to take full advantage of the flexibility of the block editor. Organizations and businesses have the ability to create dynamic landing pages with endless layouts using the group and column blocks. The centered content column and fine-tuned typography also makes it perfect for traditional blogs. Complete editor styles give you a good idea of what your content will look like, even before you publish. You can give your site a personal touch by changing the background colors and the accent color in the Customizer. The colors of all elements on your site are automatically calculated based on the colors you pick, ensuring a high, accessible color contrast for your visitors.
Tags: blog, one-column, custom-background, custom-colors, custom-logo, custom-menu, editor-style, featured-images, footer-widgets, full-width-template, rtl-language-support, sticky-post, theme-options, threaded-comments, translation-ready, block-styles, wide-blocks, accessibility-ready
Author: the WordPress team
Author URI: https://wordpress.org/
Theme URI: https://wordpress.org/themes/twentytwenty/
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

All files, unless otherwise stated, are released under the GNU General Public
License version 2.0 (http://www.gnu.org/licenses/gpl-2.0.html)

This theme, like WordPress, is licensed under the GPL.
Use it to make something cool, have fun, and share what you've learned
with others.
*/


```

--------
### wordpress loop
```php
 <?php if (have_posts() ) : while (have_posts() ) : the_post();
 
  // title,content,excerpt,tags,category,author,date,permalink,author_bio
  
  endwhile; else : ?>
		<p><?php esc_html_e( 'Sorry, There is no post' ); ?></p>
  <?php endif; ?>
```
------
### bootstrap 4 wordpress menu ထည့်နည်း

####  1 အောက်က link ကိုနှိပ်ပြီး `class-wp-bootstrap-navwalker.php` ကို ကိုယ့်ရဲ့ theme folder ထဲကူးထည့်ပါ
https://github.com/wp-bootstrap/wp-bootstrap-navwalker 

####  `<head>` ထဲမှာ အောက်က codes ကိုထည့်ပါ
```php
<nav class="navbar navbar-expand-md navbar-light bg-light" role="navigation">
  <div class="container">
    <!-- Brand and toggle get grouped for better mobile display -->
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-controls="bs-example-navbar-collapse-1" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <a class="navbar-brand" href="#">Navbar</a>
        <?php
        wp_nav_menu( array(
            'theme_location'    => 'primary',
            'depth'             => 2,
            'container'         => 'div',
            'container_class'   => 'collapse navbar-collapse',
            'container_id'      => 'bs-example-navbar-collapse-1',
            'menu_class'        => 'nav navbar-nav',
            'fallback_cb'       => 'WP_Bootstrap_Navwalker::fallback',
            'walker'            => new WP_Bootstrap_Navwalker(),
        ) );
        ?>
    </div>
</nav>
```


#### 3 functions ထဲမှာ အောက်က php codes ကိုထည့်ပါ

```php

/**
 * Register Custom Navigation Walker
 */
 
function register_navwalker(){
	require_once get_template_directory() . '/class-wp-bootstrap-navwalker.php';
}
add_action( 'after_setup_theme', 'register_navwalker' );

register_nav_menus( array(
    'primary' => __( 'Primary Menu', 'mytheme' ),
) );
```

> bootstrap 4 css နဲ့ js links တွေ သေချာအလုပ်လုပ်အောင်စစ်ပါ

------------

### the and get
အကယ်လို့  the  ဆိုရင်  echo ရိုက်စရာမလိုဘူး
အကယ်လို့  get ဆိုရင် echo ရိုက်ပါ  (မှတ်ချက် PHP echo ထည့်ရမည်)
ဥပမာ

##### the
```php
the_title();
the_author();
```

##### Get
```php
echo get_title();
echo get_the_author();
```
------
### Argument ဖြတ်ခြင်း

```php
    $args = array(
		'posts_per_page'=>'8', // post ၈ ခုပဲပြမယ်
	 );

	$query = new WP_Query( $args );
	
	// အောက်မှာ loop ကို ပြန်ချိတ်နည်း
	
 if ( $query->have_posts() ) : while ( $query->have_posts() ) : $query->the_post(); ?>
 
```
------
### URL များ
`get_template_directory_uri()` // theme folder URL
`get_stylesheet_uri()` // style.css URL

-----
### custom page ချိတ်ခြင်း
1. `page-{ကိုယ့် page နာမည်}.php` တစ်ခု create လုပ်ရမယ်
2. file ရဲ့ထိပ်နားမှာ `Template Name: Home Page` ကို comment အနေနဲ့ ထည့်ရမယ်
3. backend က page update setting နားမှာ page attribute ဆိုတာရှိတယ် အဲဒီအောက်က default template ကိုပြောင်းချိတ်ပေးရမယ်


#### 2 ရဲ့    ဥပမာ
```php
<?php
/*
// Template Name: Home Page
*/
```
---------
### Header နှင့် Footer 
`wp-head()` နှင့် `wp-footer()` သည် wordpress original codes တွေပါလာတဲ့ function ဖြစ်တယ်

`get_header()` နင့် `get_footer()`  နှင့်မမှားစေရန် သတိပြုပါ။
`get_header()` နင့် `get_footer()` ဆိုတာ ကိုယ် create  လုပ်ထားတဲ့ header.php နှင့် footer.php file တွေပဲဖြစ်ပါတယ်။

-------
### Feature Image ထည့်

Feature image ထည့်မယ်ဆို functions.php ထဲမှာ ဒီ code လေးထည့်ရမယ်
```php
add_theme_support( 'post-thumbnails' ); 
```

Frontend မှာပြန်ခေါ်သုံးမယ်ဆိုရင် `the_post_thumbnail()` လို့ခေါ်ရမယ် 

− `the_post_thumbnail('thumbnail')` // size သေးသေးလေး

− `the_post_thumbnail('medium')` // သာမာန် size

− `the_post_thumbnail('large')` // size အကြီး

− `the_post_thumbnail('full')` OR  `the_post_thumbnail()` // နဂို original size

-------

### Custom Field ထည့်

add new post ရဲ့ အပေါ်က screen options ထဲမှာ custom field ကိုသွားပြီး အမှန်ခြစ်ပေးရတယ်


**ပြန်ခေါ်သုံးမယ်ဆိုရင်**

```php
<?php echo get_post_meta(get_the_ID(), 'နာမည်', TRUE); ?>
```

-------

### wp_reset_postdata() 
page တစ်ခုတည်းမှာ loop အမျိုးအစားကွဲတွေအများကြီးပါတယ်ဆို loop တစ်ခုပြီးတိုင်း wp_reset_postdata() ကိုထည့်ပေးသင့်တယ်။ 
ဒါမှ loop တစ်ခုနဲ့တစ်ခုမငြိတော့မှာ။

--------

### Wordpress Migration ( Wordpress ရွှေ့ခြင်း )

1. database ထုတ်မယ်
2. **wp-content** ကိုကူးမယ်
3. **config.php** ထဲမှာ database user password တွေပြောင်းမယ်
4. database -> wp-options ထဲက **site url** နဲ့ **home url** ကိုပြောင်းပေးရမယ်

--------

### Wordpress Pagination
1. **posts_per_page** argument ထည့်ရမယ် `( e.g "posts_per_page" => 4 )`
2. **paged** argument ထည့်ရမယ် `( e.g "paged" => $paged )`
3. အောက်က **No 3** က codes ကို **endif;** အောက်မှာထည့်ပေးရမယ်

#### 1
```php
$args = array(
    'posts_per_page'=>4,
);
```

#### 2
```php

$paged = ( get_query_var( 'paged' ) ) ? get_query_var( 'paged' ) : 1;
$args = array(
    'paged'=> $paged,
);
```

#### 3
```php

  $total_pages = $query->max_num_pages;
  if ($total_pages > 1){
      $current_page = max(1, get_query_var('paged'));
      echo paginate_links(array(
          'base' => get_pagenum_link(1) . '%_%',
          'format' => '/page/%#%',
          'current' => $current_page,
          'total' => $total_pages,
          'prev_text'    => __('« prev'),
          'next_text'    => __('next »'),
      ));
  }  
  
```

------

## WP_QUERY

WP_Query ဆိုသည်မှာ wordpress posts တွေထဲမှာကိုယ်ထည့်ချင်တဲ့ဟာကို argument ဖြတ်ပြီးထည့်တဲ့ query ။ သူ့ကိုခေါ်သုံးမယ်ဆိုရင် `new WP_Query($arg)` 
လို့ရေးရမယ်။

ဥပမာ

```php
$arg = array(
    'post_type'=>'product', // product အမျိုးအစားကိုပဲရွေးမယ်
    'category__not_in'=> [1] // ID 1 ဆိုတဲ့ category ကိုပဲချန်ခဲ့မယ်
);

$query = new WP_Query($arg);
```

#### category အတွက် ဖြတ်နိုင်တဲ့ argument များ

* cat (int): ခေါ်သုံးမယ့် category (နံပါတ်)
* category_name (string): ခေါ်သုံးမယ့် category (နာမည်)
* category__and (array): ခေါ်သုံးမယ့် category ပေါင်း (နံပါတ် အစုလိုက်)
* category__in (array): ခေါ်သုံးမယ့် category များ (နံပါတ် အစုလိုက်)
* category__not_in (array): ဖြုတ်မယ့် category များ (နံပါတ် အစုလိုက်)

#### tag အတွက် ဖြတ်နိုင်တဲ့ argument များ

* tag (string): ခေါ်သုံးမယ့် tag (နာမည်)
* tag_id (int): ခေါ်သုံးမယ့် tag (နံပါတ်)
* tag__and (array): ခေါ်သုံးမယ့် tag ပေါင်း (နံပါတ်အစုလိုက်)
* tag__in (array): ခေါ်သုံးမယ့် tag များ (နံပါတ်အစုလိုက်)
* tag__not_in (array): ဖြုတ်မယ့် tag များ (နံပါတ်အစုလိုက်)
* tag_slug__and (array): ခေါ်သုံးမယ့် tag ပေါင်း (slug နာမည်အစုလိုက်)
* tag_slug__in (array): ခေါ်သုံးမယ့် tag များ (slug နာမည်အစုလိုက်)

-------------- 

## Meta Query
post loop argument ထဲမှာကို custom field ရဲ့ value နဲ့တိုက်စစ်ပြီးတော့ filter လုပ်လို့ရပါတယ်

- `=` : equals
- `!=` : not equals
- `>` : greater than
- `>=` : greater than or equal to
- `<` : less than
- `<=` : less than or equal to
- `IN` : in a given array
- `NOT IN` : not in a given array
- `BETWEEN` : between two given values
- `NOT BETWEEN` : not between two given values
- `EXISTS` : the meta key exists
- `NOT EXISTS` : the meta key does not exist

ဥပမာ 

```php
$args = [
    'post_type' => 'post',
    'meta_query' => [
      [
	'key' => 'price',
	'value' => 1000,
	'compare' => '>='
      ]
    ]
  ];
```

အပေါ်က arguments ရဲ့ဆိုလိုချက်က စျေးနူန်း 1000 နဲ့ညီတာသို့မဟုတ် ကြီးတာကို ဆွဲထုတ်ပေးမှာဖြစ်ပါတယ်။  
