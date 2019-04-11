# TIL AMP

Today I learned about AMP

## Topics

+ [hello-amp](https://github.com/hahnah/til-amp/tree/master/hello-amp) : My first AMP project along with official tutorial.
+ [amp-story](https://github.com/hahnah/til-amp/tree/master/amp-story) : AMP Story tutorial

## Development

### Templete

```html
<!doctype html>
<html amp lang="en">
  <head>
    <meta charset="utf-8">
    <script async src="https://cdn.ampproject.org/v0.js"></script>
    <title>Hello, AMPs</title>
    <link rel="canonical" href="http://example.ampproject.org/article-metadata.html">
    <meta name="viewport" content="width=device-width,minimum-scale=1,initial-scale=1">
    <script type="application/ld+json">
      {
        "@context": "http://schema.org",
        "@type": "NewsArticle",
        "headline": "Open-source framework for publishing content",
        "datePublished": "2015-10-07T12:02:41Z",
        "image": [
          "logo.jpg"
        ]
      }
    </script>
    <style amp-boilerplate>body{-webkit-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-moz-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-ms-animation:-amp-start 8s steps(1,end) 0s 1 normal both;animation:-amp-start 8s steps(1,end) 0s 1 normal both}@-webkit-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-moz-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-ms-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-o-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}</style><noscript><style amp-boilerplate>body{-webkit-animation:none;-moz-animation:none;-ms-animation:none;animation:none}</style></noscript>
    <style amp-custom>
      /* any custom style goes here */
    </style>
  </head>
  <body>
    <h1>Welcome to the mobile web</h1>
  </body>
</html>
```

### Preview

1. `$ python -m SimpleHTTPServer` to run a local server.
2. Open `localhost:8000/-path-/index.html`.  

### Debug AMP

1. `$ python -m SimpleHTTPServer` to run a local server.
2. Open `localhost:8000/-path-/index.html#development=1`.
3. Open ChromeDevTools.

## Author

hahnah

## License

MIT &copy; 2019, hahnah