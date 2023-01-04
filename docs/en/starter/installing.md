---
layout: page
title: Installing epub.js
menu: starter
lang: en
redirect_from: "/starter/installing.html"
---

# Installing & Building

Clone the repository, install dependencies and build the library:

```
$ git clone git@github.com:ig3/epub.js.git
$ cd epub.js
$ npm install
$ npm run prepare

```

# Using

Load jsZip from CDN and epub.js from the dist directory of the repository.

```
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.1.5/jszip.min.js></script>
  <script src="../dist/epub.min.ms"></script>
```

jsZip is only required if you will be using zipped ePub files. If it is
required, it must be loaded before epub.js.


Set up an element to render to:

```
  <div id="epub_container"></div>
```

Load and render the ePub:

```
<script>
  const book = ePub("url/to/book.epub");
  const rendition = book.renderTo(
    'epub_container',
    { width: 600, height: 400 }
  );
  const displayed = rendition.display();
```

###  [Next: Examples ](/{{ page.lang }}/starter/examples.html)
