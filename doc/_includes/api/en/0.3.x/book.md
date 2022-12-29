<h3 id="book">Book</h3>

The Book object encapsulates an epub book. It has methods for opening,
closing, rendering and navigating within the book.

<h4 id="book.constructor">Constructor: new Book(url, [options])</h4>

Constructs a new epubjs Book object for the book at the given url.

```js
const book = new Book('https://epub.server.example.com/path/to/book.epub');
```
Arguments:
 
 * `url` (string) - The URL at which to request the epub book.
 * `options` (object) - Optional options object to configure the book.

Returns: an instance of Book.

The `options` argument can have the following fields:

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


<h4 id='book.methods'>Methods</h4>


<h5 id="book.open">open(input, what)</h5>

Open an epub from a URL or ArrayBuffer.

Returns: Promise that resolves when the book has been loaded.

Arguments:

 * input (string \| ArrayBuffer) - a URL or path string or an ArrayBuffer.
 * what (string) - 'binary', 'base64', 'epub', 'opf', 'json' or 'directory'
   - force opening as a certain type. **Default**: ???

<h5 id="book.load">load(path></h5>

Load a resource from the Book.

Returns: a Promise that resolves to the requested resource.

Arguments:

 * path (string) - path to the resource to load.

<h5 id="book.resolve">resolve(path, [absolute])</h5>

Resolve a path to its absolute position in the Book.

Returns: (string) the resolved path string

Arguments:

 * path (string) - the path to resolve
 * absolute (boolean) - force resolving the full URL if true

<h5 id="book.canonical">canonical(path)</h5>

Get a canonical link to a path.

Returns: (string) the canonical path string

Arguments:

 * path (string) - ???

<h5 id="book.section">section(target)</h5>

Get a Section of the Book from the Spine.

Alias for: book.spine.get

Returns: (Section) the target Section of the Book

Arguments:

 * target (string) - the section identifier


<h5 id="book.renderto">renderTo(element, [options])</h5>

Render the book to a DOM element.

Returns: (Rendition) - the rendition object of the rendered book.

Arguments:

 * element (element \| string) - The DOM element or string (???) to add the
   rendition to.
 * options (object) - The options for rendering the book.

The `options` argument can have the following fields:

 * ???

<h5 id="book.setRequestCredentials">setRequestCredentials(credentials)</h5>o

Set if request should use withCredentials.

Returns: ???

Arguments:

 * credentials (boolean) - true of request should use credentials???

How are the actual credentials set? 

<h5 id="book.setRequestHeaders">setRequestHeaders(headers)</h5>

Set headers that should be included with the request.

Returns: ???

Arguments:

 * headers (object) - the set of headers to include

<h5 id="book.coverUrl">coverUrl()</h5>

Get the URL of the cover image.

Returns: (string) the URL of the cover image

Arguments:

<h5 id="book.getRange">getRange(cfiRange)</h5>

Find a DOM Range for a given CFI Range.

Returns: (Range) - the DOM Range corresponding to the given CFI Range


<h5 id="book.key">key([identifier])</h5>

Generated the Book Key using the identifier in the manifest or other string
provided.

Returns: (string) the generated key

Arguments:

 * identifier (string) - an identifier to be used insead of the identifier
   in the manifest. **Default**: the identifier in the manifest.

<h5 id="book.destroy">destroy()</h5>

Destroy the Book instance and all associated objects.

Returns: undefined

Arguments:

 * none
