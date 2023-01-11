<h2 id="book">Book</h2>

The Book object encapsulates an EPUB Package: a collection of resources
constituting a rendition of an EPUB Publication. It provides methods for
loading the EPUB Package data, rendering a view of it in the web browser,
and navigating the view through the contents.

<h3 id="book.constructor">Constructor: new Book(url, [options])</h3>

Constructs a new epubjs Book object for the book at the given url.

```js
const book = new Book('https://epub.server.example.com/path/to/book.epub');
```
Arguments:
 
 * `url` (string) - The EPUB Container data or a URL from which an
 [EPUB OCF ZIP Container](https://www.w3.org/publishing/epub/epub-ocf.html#sec-container-zip),
 [EPUB Package Document](https://www.w3.org/publishing/epub/epub-packages.html#sec-package-doc),
 [Publication Manifest](https://www.w3.org/TR/pub-manifest/) or possibly
 [Readium Web Publication Manifest](https://readium.org/webpub-manifest/)
 (the code only says 'manifest' and that it is JSON data - it doesn't say
 what specification the data conforms to)


 the EPUB Container data or the Package can be obtained.
 * `options` (object) - An optional options object to configure the book.

Returns: an instance of Book.

The `options` argument can have the following fields:

 * `manager` (string\|object) - 'default', 'continuous' or a viewManager
   object.
 * `requestMethod` (function) - a function to use instead of the inbuilt request function for requesting resources.
 **Default**: utils/request
 * `requestCredentials` (boolean) - Send the xhr request with Credentials if truthy.
 **Default**: undefined
 * `requestHeaders` (object) - send the xhr request headers.
 **Default**: undefined
 * `encoding` (string) - optional to pass 'binary' or 'base64' to archived Epubs.
 **Default**: binary
 * `replacements` (string) - use 'base64', 'blobUrl' or 'none' for replacing
 assets in archived Epubs.
 **Default**: 'none'
 * `canonical` (function) - function to determine canonical urls for a path.
 **Default**: undefined.
 * `openAs` (string) - optional string to determine the input type.
 **Default**: undefined.


There are two view managers available: default and continuous.

The default view manager provides a paginated display. One chapter /
section at a time is displayed, split into pages.

The continuous view manager provides a continuous display presenting one
chapter / section at a time, complete with vertical scrolling.


<h3 id='book.methods'>Methods</h3>


<h4 id="book.open">open(input, what)</h4>

Open an epub from a URL or ArrayBuffer.

Returns: Promise that resolves when the book has been loaded.

Arguments:

 * input (string \| ArrayBuffer) - a URL or path string or an ArrayBuffer.
 * what (string) - 'binary', 'base64', 'epub', 'opf', 'json' or 'directory'
   - force opening as a certain type. **Default**: ???


<h5>what = 'binary'</h5>

`input` should be a zip file in the form of a String, Array of bytes,
ArrayBuffer, Uint8Array, Buffer, Blob or a Promise returning one of these.

The data is unzipped using [JSZip](https://stuk.github.io/jszip/).

The type of input varies with `what`:

 * binary
 * base64
 * epub
 * opf
 * json
 * directory
 * undefined


<h4 id="book.load">load(path></h4>

Load a resource from the Book.

Returns: a Promise that resolves to the requested resource.

Arguments:

 * path (string) - path to the resource to load.

<h4 id="book.resolve">resolve(path, [absolute])</h4>

Resolve a path to its absolute position in the Book.

Returns: (string) the resolved path string

Arguments:

 * path (string) - the path to resolve
 * absolute (boolean) - force resolving the full URL if true

<h4 id="book.canonical">canonical(path)</h4>

Get a canonical link to a path.

Returns: (string) the canonical path string

Arguments:

 * path (string) - ???

<h4 id="book.section">section(target)</h4>

Get a Section of the Book from the Spine.

Alias for: book.spine.get

Returns: (Section) the target Section of the Book

Arguments:

 * target (string) - the section identifier


<h4 id="book.renderto">renderTo(element, [options])</h4>

Render the book to a DOM element.

Returns: (Rendition) - the rendition object of the rendered book.

Arguments:

 * element (element \| string) - The DOM element (element) or element ID
   (string) to add the rendition to.
 * options (object) - The options for rendering the book.

The `options` are passed to the Rendition constructor. See Rendition for
details of the options.

A new Rendition is constructed and then attached to the given element by
appending it as a child element. This would typically be to a `div` element
but other elements are possible.

<h4 id="book.setRequestCredentials">setRequestCredentials(credentials)</h4>o

Set if request should use withCredentials.

Returns: ???

Arguments:

 * credentials (boolean) - true of request should use credentials???

How are the actual credentials set? 

<h4 id="book.setRequestHeaders">setRequestHeaders(headers)</h4>

Set headers that should be included with the request.

Returns: ???

Arguments:

 * headers (object) - the set of headers to include

<h4 id="book.coverUrl">coverUrl()</h4>

Get the URL of the cover image.

Returns: (string) the URL of the cover image

Arguments:

<h4 id="book.getRange">getRange(cfiRange)</h4>

Find a DOM Range for a given CFI Range.

Returns: (Range) - the DOM Range corresponding to the given CFI Range


<h4 id="book.key">key([identifier])</h4>

Generated the Book Key using the identifier in the manifest or other string
provided.

Returns: (string) the generated key

Arguments:

 * identifier (string) - an identifier to be used insead of the identifier
   in the manifest. **Default**: the identifier in the manifest.

<h4 id="book.destroy">destroy()</h4>

Destroy the Book instance and all associated objects.

Returns: undefined

Arguments:

 * none
