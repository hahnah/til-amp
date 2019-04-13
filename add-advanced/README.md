# Add Advanced AMP Features

See [official tutorial](https://amp.dev/ja/documentation/guides-and-tutorials/start/add_advanced/index.html).

## AMP Component Kinds

+ built-in
  + e.g. `amp-img`, `amp-pixel`
+ extended
  + e.g. `amp-video`, `amp-story`, `amp-ad`
  + Write like `<script async custom-element="amp-video" ...` in `<head>` section to use
+ experimental

#### Exended AMP Components used in this TIL

+ amp-ad
+ amp-youtube
+ amp-fit-text
+ amp-carousel
+ amp-analytics
+ amp-sidebar

## amp-ad

An extended component.

## amp-youtube

An extended component.

### Required script

```html
<script async custom-element="amp-youtube" src="https://cdn.ampproject.org/v0/amp-youtube-0.1.js"></script>
```

### Usage

```html
<amp-youtube
  data-videoid="npum8JsITQE"
  layout="responsive"
  width="480"
  height="270">
  <div fallback>
    <p>The video could not be loaded.</p>
  </div>
</amp-youtube>
```

## amp-twitter

### Required script

```html
<script async custom-element="amp-twitter" src="https://cdn.ampproject.org/v0/amp-twitter-0.1.js"></script>
```

### Usage

```html
<amp-twitter
  width="486"
  height="657"
  layout="responsive"
  data-tweetid="1116339802360516608">
</amp-twitter>
```

## amp-fit-text

See [https://amp.dev/ja/documentation/examples/components/amp-fit-text/index.html?format=websites](https://amp.dev/ja/documentation/examples/components/amp-fit-text/index.html?format=websites) for details.

### Required script

```html
<script async custom-element="amp-fit-text" src="https://cdn.ampproject.org/v0/amp-fit-text-0.1.js"></script>
```

### Usage

```html
<amp-fit-text width="400" height="75" layout="responsive" max-font-size="42">
      Big, bold article quote goes here.
    </amp-fit-text>

    <amp-fit-text width="400" height="400" layout="responsive" max-font-size="42">
       Hello!
    </amp-fit-text>

    <amp-fit-text width="400" height="75" layout="responsive" max-font-size="42">
        And the Raven, never flitting, still is sitting, still is sitting. On the pallid bust of Pallas just above my chamber door; And his eyes have all the seeming of a demon’s that is dreaming, And the lamp-light o’er him streaming throws his shadow on the floor; And my soul from out that shadow that lies floating on the floor. Shall be lifted—nevermore!
    </amp-fit-text>
```

![amp-fit-text](amp-fit-text.png)

## amp-carousel

I don't know why the tutorial doesn't work well.

### Required script

```html
<script async custom-element="amp-carousel" src="https://cdn.ampproject.org/v0/amp-carousel-0.1.js"></script>
```

### Usage

#### Poor version

```html
<amp-carousel layout="fixed-height" height="168" type="carousel" >
  <amp-img src="mountains-1.jpg" width="300" height="168"></amp-img>
  <amp-img src="mountains-2.jpg" width="300" height="168"></amp-img>
  <amp-img src="mountains-3.jpg" width="300" height="168"></amp-img>
</amp-carousel>
```

#### Responsive version

To make it responsive: 

+ `type="slides"` in `amp-carousel`
+ `layout="responsive"` in `amp-carousel` and sub `amp-img`
  + **NOTE** `"fixed-height"` layout requires only `height`, but `"responsive"` layout does both of `width` and `height`

```html
<amp-carousel layout="responsive" width="300" height="168" type="slides" >
  <amp-img src="mountains-1.jpg" layout="responsive" width="300" height="168"></amp-img>
  <amp-img src="mountains-2.jpg" layout="responsive" width="300" height="168"></amp-img>
  <amp-img src="mountains-3.jpg" layout="responsive" width="300" height="168"></amp-img>
</amp-carousel>
```

#### Loop & Autoplay

+ **Loop**: Just write `loop` field
+ **Autoplay**: Write `autoplay` & `delay="2000"`, which means autoplay with intevel of 2000 msec

```html
<amp-carousel layout="responsive" width="300" height="168" type="slides" loop delay="2000" >
  <amp-img src="mountains-1.jpg" layout="responsive" width="300" height="168"></amp-img>
  <amp-img src="mountains-2.jpg" layout="responsive" width="300" height="168"></amp-img>
  <amp-img src="mountains-3.jpg" layout="responsive" width="300" height="168"></amp-img>
</amp-carousel>
```

#### Mixed Caroucel Content

Mix of `amp-img`, `amp-ad`, and `amp-fit-text`:

```html
<amp-carousel layout="fixed-height" height="250" type="carousel" >
  <amp-img src="blocky-mountains-1.jpg" width="300" height="250"></amp-img>

  <amp-ad width="300" height="250"
      type="doubleclick"
      data-slot="/35096353/amptesting/image/static">
    <div placeholder>This ad is still loading.</div>
  </amp-ad>

  <amp-fit-text width="300" height="250" layout="fixed">
    Big, bold article quote goes here.
  </amp-fit-text>
</amp-carousel>
```

**NOTE** Add this style to `<style amp-custom>` to ensure the `amp-fit-text` and `amp-carousel` components work together safely:

```css
amp-fit-text {
    white-space: normal;
}
```

**NOTE** In above code `amp-ad` includes a compnent with `placeholer` attribute.  
There is a difference between `placeholder` and `fallback`.

+ `placeholder`: Placeholder elements appear in place of the parent element, **while it is loading**.
+ `fallback`: Fallback elements appear **when the parent element fails to load**, i.e. if there was no ad available.

## amp-analytics

### Required script

```html
<script async custom-element="amp-analytics" src="https://cdn.ampproject.org/v0/amp-analytics-0.1.js"></script>
```

### Usage

Write at the end of the `body`:

```html
<amp-analytics type="googleanalytics">
<script type="application/json">
{
  "vars": {
    "account": "UA-YYYY-Y"
  },
  "triggers": {
    "default pageview": {
      "on": "visible",
      "request": "pageview",
      "vars": {
        "title": "Name of the Article"
      }
    }
  }
}
</script>
</amp-analytics>
```

**NOTE** `amp-pixel` is also available. It's seems simpler than `amp-analytics`.


## Link back home

Place a link back home in `header`:

```html
<header class="headerbar">
  <a href="homepage.html">
    <amp-img class="home-button" src="icons/home.png" width="36" height="36"></amp-img>
  </a>
 <div class="site-name">News Site</div>
</header>
```

```css inline css example
.home-button {
  margin-top: 8px;
}
.headerbar {
  height: 50px;
  position: fixed;
  z-index: 999;
  top: 0;
  width: 100%;
  display: flex;
  align-items: center;
}
.site-name {
  flex: 1;
  margin-left: -36px;
}
article {
  margin-top: 50px;
}
```

## amp-sidebar

Implemnt a navigation menu using `amp-sidebar`.

### Required script

```html
<script async custom-element="amp-sidebar" src="https://cdn.ampproject.org/v0/amp-sidebar-0.1.js"></script>
```

### Usage

Place a hamburger button:

```html
<header class="headerbar">
  <div role="button" on="tap:sidebar1.toggle" tabindex="0" class="hamburger">☰</div>
  <div class="site-name">News Site</div>
</header>
```

Place `amp-sidebar` just after the `</header>` in `body` tag.
Sidebar menu appears when the hamburger button is clicked.

```html
<amp-sidebar id="sidebar1" layout="nodisplay" side="left">
  <div role="button" aria-label="close sidebar" on="tap:sidebar1.toggle" tabindex="0" class="close-sidebar">✕</div>
  <ul class="sidebar">
    <li><a href="#">Example 1</a></li>
    <li><a href="#">Example 2</a></li>
    <li><a href="#">Example 3</a></li>
  </ul>
</amp-sidebar>
```

```css inline css example
.hamburger {
  padding-left: 10px;
}
.sidebar {
  padding: 10px;
  margin: 0;
}
.sidebar > li {
  list-style: none;
  margin-bottom:10px;
}
.sidebar a {
  text-decoration: none;
}
.close-sidebar {
  font-size: 1.5em;
  padding-left: 5px;
}
```

## Adding Fonts

An example to use `Raleway` font.

### Required link

Add an css link to `header`:

```html
<link rel="stylesheet" type="text/css" href="https://fonts.googleapis.com/css?family=Raleway">
```

Update custom style of `body`:

```css
body {
  width: auto;
  margin: 0;
  padding: 0;
  font-family: 'Raleway', sans-serif;
}
```