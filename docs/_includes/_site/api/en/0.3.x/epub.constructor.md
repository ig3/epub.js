<h3 id='epub.constructor' class='h2'>ePub(url, options)</h3>

<div class="doc-box doc-info" markdown="1">
This API is available.
</div>

This is a factory function for creating a new epub Book.

It creates the book as:

```
  const book = new Book(url, options);
```

The ePub function object has additional properties:

 * Book
 * Rendition
 * Contents
 * CFI - epubcfi
 * utils

These access the corresponding objects of the epub.js library.
