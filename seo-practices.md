# SEO practices

- [1- Add text inside every html element](#add-text) 
- [2- Add label tag for every input tag](#add-label) 
- [3- Add rel to every a tag with target="_blank"](#add-rel) 
- [4- Add alt to every image tag](#add-alt) 

## 1 - Add text inside every html element, e.g `<a>` `<button>` <a name="add-text"></a>

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

--------
## 2 - Add Label tag for every input tag  <a name="add-label"></a>


Add label tag for every input tag

### Bad
```
<input class="form-control" name="s" id="search"> 
```

### Good
```
<div class="form-group">
   <label for="search">Search</label>
   <input class="form-control" name="s" id="search"> 
</div>
```

---------

## 3 - Add rel to every a tag with target="_blank" <a name="add-rel"></a>

Add rel attribute to every `<a>` tag which includes target="_blank" attribute

### Bad 
```
<a href="https://example.com" target="_blank">Example</a>
```

### Good 
```
<a href="https://example.com" rel="noreferrer noopener" target="_blank">Example</a>
```

---------

## 3 - Add alt to every image tag <a name="add-alt"></a>

Add alt attribute for every image tag

### Bad 
```
<img src="https://picsum.photos/2000">
```

### Good 
```
<img src="https://picsum.photos/2000" alt="Nature Image">
```


