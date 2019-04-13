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

## amp-sidebar
