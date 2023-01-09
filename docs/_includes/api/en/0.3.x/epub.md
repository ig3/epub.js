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

The [epub.js readme](https://github.com/futurepress/epub.js) shows an
example of a URL with extension 'opf' which suggests that it would yield a
[Package Document](https://www.w3.org/publishing/epub/epub-packages.html#sec-package-doc),
rather than an
[EPUB Package](https://www.w3.org/publishing/epub/epub-packages.html),
though this isn't stated specifically in the documentation.

Looking at the code in book.js, there is a complex heuristic to determine
the type of 'the input passed to open'. Possible types are:

 * base64
 * binary
 * directory
 * epub
 * opf
 * json

Type base64 is determined based on the value of the encoding option (if it
is 'base64').

Type binary is concluded if the value of the url parameter is not a string.
Presumably it can be the data itself, rather than a URL from which the data
can be obtained, but this remains to be confirmed.

The other types are determined based on the 'extension' found in the 'url'.

Type directory if no extension is found.

Types epub, opf or json if those extensions are found.

Alternatively, the type may be specified in the openAs option.

The supported values are:

 * 'binary' - The 'url' must be the content of a zipped EPUB Document.
 * 'base64' - As above, but the data is base64 encoded.
 * 'epub' - The 'url' is the URL of an EPUB Package file.
 * 'opf' - The 'url' is the URL of an Open Packaing Format file.
 * 'manifest' - The 'url' is the URL of a manifest - type json.
 * otherwise - The 'url' is the URL of an 'epub container'

When opening an epub file or url, the path of the OPF file is obtained from
the EPUB Package file and this is opened as when the URL of the OPF file is
provided directly. It may be that, binary and base64 aside, the url options
other than opf and ways to obtain the OPF url.

Every EPUB Package contains an Open Packaging Format file.

The type 'manifest' corresponds to a URL with extension 'json'. If the URL
has extension 'json', it must be the URL of a manifest file, which is JSON
data.

It isn't immediately obvious what an 'epub container' is. The term is taken
from the comment to the openContainer method of book.js. It appears it is
an XML document of some sort.

when an epub document is opened, after it is unarchived, openContainer
method opens the 'epub container', from which the path to the package file
is obtained and this (the OPF) is opened. So, it seems the 'epub container'
is fundamental to an EPUB Package.

There is an archived flag on the book object. It is set to true for binary,
base64 and epub files. This might be used to indicate that the zip file
(a.k.a. archive) of the EPUB Package has been loaded, rather than just a
part of it.

The issue is a bit confused because the archive is a zip file and it is not
immediately obvious if the archived flag indicates that the data is a zip
archive that must be unarchived or if it means that the data was a zip
archive and it has been unarchived. 


<h3 id='epub.methods'>Methods</h3>

The ePub function object has additional properties:

 * Book
 * Rendition
 * Contents
 * CFI - epubcfi
 * utils

These access the corresponding objects of the epub.js library.


