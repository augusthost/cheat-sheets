# SEO practices

Add text inside every html element, e.g `<a>` `<button>`

### Bad

```html
<a href="/" class="brand-logo"><img src="https://website.com/logo.png"></a>
```

```html
<a href="https://facebook.com"><i class="fa fa-facebook"></i></a>
```

### Good


```html
<a href="/" class="brand-logo"><img src="https://website.com/logo.png"> <span class="seo-hidden-text">Website Name</span></a>
```

```html
<a href="https://facebook.com"><i class="fa fa-facebook"></i> <span class="seo-hidden-text">Facebook</span></a>
```

Style for "seo-hidden-text" class
```css
.seo-hidden-text{
position:absolute;
text-indent:-9999px;
}
```
