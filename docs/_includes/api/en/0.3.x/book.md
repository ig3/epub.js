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


<h3 id='book.attributes'>Attributes</h3>

<h4 id="book.path">path</h4>

path is an instance of Path for the URL the Open Packaging Format XML file
or the Manifest URL. Its resolve method is used to resolve paths. 

<h3 id='book.methods'>Methods</h3>


<h4 id="book.open">open(input, what)</h4>

Open an epub from a URL or ArrayBuffer.

Returns: Promise that resolves when the book has been loaded.

Arguments:

 * input (string \| ArrayBuffer) - a URL or path string or an ArrayBuffer.
 * what (string) - 'binary', 'base64', 'epub', 'opf', 'json' or 'directory'
   - force opening as a certain type. **Default**: ???



<h5>what</h5>
<h6>default</h6>
If what isn't specified, the default is as follows:

If the book instance was created with option encoding set to base64, then
what is set to 'base64'.

Otherwise, if `input` is not of type string, then what is set to 'binary'.

Otherwise, if the path in `input` does not end with a filename with an
extension, then what is set to 'directory'

Otherwise, if the path in `inputs` ends with extension 'epub' then type is
set to 'epub'.

Otherwise, if the path in `inputs` ends with extension 'opf' then type is
set to 'opf'.

Otherwise, if the path in `inputs` ends with extension 'json' then type is
set to 'manifest'.

<h6>input required for each what value</h6>

The type of input varies with the value of `what`:

 * binary
 * base64
 * epub
 * opf
 * json
 * directory
 * undefined

If the value of `what` is 'binary' then the value of `input` should be the
data of an EPUB
[OCF ZIP Container](https://www.w3.org/publishing/epub/epub-ocf.html#sec-container-zip).
This is typically a file with extension '.epub'.
The data is unzipped using [JSZip](https://stuk.github.io/jszip/).
According to the documentation of JSZip, the input can be a String, Array
of bytes, ArrayBuffer, Uint8Array, Buffer, Blob or a Promise returning one
of these.

If the value of `what` is 'base64' then the value of `input` should be a
base64 encoded string which, when decoded, yields the data of an EPUB OCF
ZIP Container: an epub file, as for 'binary'.

If the value of `what` is 'epub' then the value of `input` should be a URL
from which an EPUB OCF ZIP Container can be retrieved.

If the value of `what` is 'opf' then the value of `input` should be a URL
from which an EPUB 
[Package Document](https://www.w3.org/publishing/epub3/epub-packages.html#sec-package-doc)
can be retrieved.

If the value of `what` is 'json' then the value of `input` should be a URL
from which a
[Readium Web Publication Manifest](https://readium.org/webpub-manifest/)
can be retreived, or perhaps some other very similar manifest. It is not
clear exactly what manifests epub.js is compatible with.

If the value of `what` is 'directory' or undefined then the value of `input`
should be a URL that is the path of the root directory of an EPUB
[OCF Abstract Container](https://www.w3.org/publishing/epub/epub-ocf.html#sec-container-abstract)
directory tree, from which the various contents can be retrieved by
requests to the specific content and, in particular, with an
[EPUB 3 Container File](https://www.w3.org/publishing/epub3/epub-ocf.html#sec-container-metainf-container.xml)
at the sub-path 'META_INFO/container.xml'.



<h4 id="book.openEpub">openEpub(data, encoding)</h4>

Open an archived epub.

Arguments:

 * `data` - (binary) - The data of the EPUB file.
 * `encoding` - (string) - should be blank or 'base64'

Returns: a Promise that resolves to undefined after the epub is opened.

<h4 id="book.openContainer">openContainer(url)</h4>

Get the full path of the root file of the first rendition listed in the
Container File of the EPUB.

See:
[EPUB 3 Container File](https://www.w3.org/publishing/epub3/epub-ocf.html#sec-container-metainf-container.xml)

Arguments:

 * `url` - (string) - the URL of the container

Returns: a Promise that resolves to the resolved path from the `full-path`
attribute of the first rootfile element of the container, after the
container is opened.

The url may be the full URL of the Container File if opening from an
unarchived source or the full path or relative path (e.g.
'META-INF/container.xml') from the root of the container if opening from an
archived source (e.g. a .epub file).

Note: a container document might have more than one rootfile elements
within its rootfiles element. This method provides no means to access any
but the first rootfile element.

In the case of opening an epub archive, the resolved path might be
'/EPUB/content.opf'. In any case, the path to the
[Package Document](https://www.w3.org/publishing/epub3/epub-packages.html#sec-package-doc)
that describes the rendition.

<h4 id="book.openPackaging">openPackaging(url)</h4>

Open the 
[Package Document](https://www.w3.org/publishing/epub3/epub-packages.html#sec-package-doc)
of the EPUB Rendition.

Arguments:

 * `url` - (string) - the URL of the Package Document.

Returns: a Promise that resolves to undefined after the Package Document
has been opened.

In particular, this loads the manifest, metadata, spine, cover, resources
and pageList elements of the Package Document.

<h4 id="book.openManifest">openManifest(url)</h4>

Open the manifest JSON.

In this case the manifest is probably an instance of a
[Readium Web Publication Manifest](https://readium.org/webpub-manifest/),
or something compatible.

See [Issue 822](https://github.com/futurepress/epub.js/issues/822) for some
background.

See [Readium EPUB Profile](https://readium.org/webpub-manifest/profiles/epub.html)

See [readium/webpub-manifest](https://github.com/readium/webpub-manifest)

It isn't clear from the documentation, what the intended or actual use of
this method is. The epub.js examples folder includes one example using this
method, but the URL to the manifest now yields a 404 error. Possibly
because the Readium project has been somewhat terminated by Google, if I
understand correctly. Or maybe it is just the Readium Chrome Application
that is deprecated and other parts of the Readium suite are still supported
/ used ongoing.

See [Readium Desktop](https://www.edrlab.org/software/readium-desktop/). It
seems Readium Desktop is the basis of Thorium Reader which remains actively
developed. So, Readium isn't dead yet.

See [Web-Pub](https://www.w3.org/TR/wpub/#webpub). this also has a manifest
and it may be that epub.js is compatible with the web-pub manifest.

See [Packaged Web Publications](https://www.w3.org/TR/pwpub/). Might
epub.js have some compatibility with these?

Arguments:

 * `url` - (string) the URL of the manifest document.

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

Returns:
 * undefined if path is falsy
 * path, unmodified, if it includes '://' (assumed to be absolute)

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
