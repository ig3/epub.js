<h2 id="epub">ePub(url, [options])</h2>

Creates an epub.js Book object from an epub file obtained from the given
URL.

The epub file format is specified by
[EPUB 3.2](https://www.w3.org/publishing/epub/epub-spec.html).

The ePub() function is a top-level/global function exported by the epub module.

Constructs a new Book object for the epub book at the given url.

```js
const book = ePub('https://epub.server.example.com/path/to/book.epub');
```

It creates the book as:

```js
  new Book(url, options);
```

<h3 id='epub.methods'>Methods</h3>

The ePub function object has additional properties:

 * Book
 * Rendition
 * Contents
 * CFI - epubcfi
 * utils

These access the corresponding objects of the epub.js library.


