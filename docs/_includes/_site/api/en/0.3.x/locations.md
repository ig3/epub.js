<h2 id="locations">Locations</h2>

The Locations object deals with locations within a book.

The book is divided into an array of ranges with a maximum size, by
default, 150 characters. For each such range an epubcfi is generated and
appended to the array of 'locations'. 

<h3 id="locations.constructor">Constructor: new Rendition(book, [options])</h3>

Constructs a new Rendition object for the locations at the given Book.

```js
const locations = new Rendition(book, [options]);
```
Arguments:
 
 * `book` (Book) - The instance of Book to be rendered.
 * `options` (object) - Optional options object to configure the locations.

Returns: an instance of Rendition.

The `options` argument can have the following fields:

 * `width` (number) - The width of the rendered book.
 **Default**: undefined
 * `height` (number) - The height of the rendered book.
 **Default**: undefined
 * `ignoreClass` (string) - class for the cfi parser to ignore.
 **Default**: undefined
 * `manager` (string\|function\|object) - The manager to manage the
   locations.
 **Default**: 'default'
 * `view` (string\|function) - ???
 **Default**: 'iframe'
 * `layout` (string) - layout to force.
 **Default**: undefined.
 * `spread` (string) - force spread value.
 **Default**: undefined.
 * `minSpreadWidth` (number) - overridden by spread:none(never)/both(always).
 **Default**: undefined.
 * `stylesheet` (string) - url of stylesheet to be injected.
 **Default**: undefined.
 * `resizeOnOrientationChange` (boolean) - false to disable orientation events.
 **Default**: undefined.
 * `script` (string) - URL of script to be injected.
 **Default**: undefined.


<h3 id='locations.methods'>Methods</h3>


<h4 id="locations.generate">generate(chars)</h4>

Generate the array of locations.

Returns: (Promise) - a promise that resolves to the arry of locations when
it has been generated.

Arguments:

 * `chars` (number) - the number of chars in each location.

All content documents listed in the spine of the book are parsed. Their
text content is split into segments of `chars` characters and a Range is
produced for each segment. These ranges are serialized to EpubCFI strings
and accumulated into the `locations` array. Thus, the `locations` array is
an array of EpubCFI strings that specify the ranges of characters, each
`chars` characters long.

<h4 id="locations.cfiFromPercentage">cfiFromPercentage(percentage)</h4>

Returns: (string) the epubcfi of the location range that begins at
approximately the given percentage through the book.

Arguments:

 * percentage (number) - a ratio of distance from the start of the book to
   the total length of the book, in characters. A number in the range 0 to
   1.

The epubcfi is only approximately at the given percentage through the book.
The book is divided into ranges of 150 characters. The returned epubcfi
should be for the range that includes the character at the given
percentage.

<h4 id="locations.parse">parse(contents, cfiBase, chars)</h4>

Parse the contents of a single section (spine item) of the book, generating
an array of ranges of maximum length 150 characters.

Returns: (string[]) - an array of epubcfi strings defining ranges of the
content. Each range is `chars` characters long except the last one, which
may be shorter.

Arguments:

 * contents (???) - the content document of the 'chapter' (item from the
   spine) in the form or ???
 * cfiBase (string) - The leading part of the epubcfi that identifies the
   item from the spine that is being processed.
 * chars (integer) - the maximum number of characters in a range.
   **Default**: 150.

The content must have a `body` element. The text nodes within the body
element are processed. 

<h4 id="locations.attachTo">attachTo(element)</h4>

Attach the locations container to the given element in the DOM. The
container must be attached before the rendering can begin.

Returns: Promise that resolves when the container has been attached.

Arguments:

 * element (element) - The DOM element to which the container should be
   attached.

<h4 id="locations.clear">clear()</h4>

Clear the rendered views.

Returns: ???

Arguments:

 * none

<h4 id="locations.currentLocation">currentLocation()</h4>

Get or Set the CurrentLocation object.

Returns: (displayedLocation\|Promise) The displayedLocation object with the
current location or a Promise that resolves to this.

Arguments:

 * none

<h4 id="locations.destroy">destroy()</h4>

Remove and Clean Up the Locations instance.

Returns: ???

Arguments:

 * none

