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

Get the CurrentLocation object.

Returns: (displayedLocation\|Promise) The displayedLocation object with the
current location or a Promise that resolves to this.

Arguments:

 * none

<h4 id="locations.destroy">destroy()</h4>

Remove and Clean Up the Rendition.

Returns: ???

Arguments:

 * none

<h4 id="locations.direction">direction(direction)</h4>

Adjust the direction of the locations.

Returns: ???

Arguments:

 * direction (string) - the direction for the locations.

<h4 id="locations.display">display(target)</h4>

Display a point in the book.

The request will be added to the rendering Queue, so it will wait until the
book is opened, rendering started and all previously queued rendering tasks
have finished.

Returns: (Promise) a promise that resolves to ??? when the given target has
been displayed in the locations.

Arguments:

 * target (string) - URL, EpubCFI or floating point number in the range 0
   to 1, that determines the location in the book to be displayed.


<h4 id="locations.flow">flow(flow)</h4>

Adjust the flow of the locations to paginated or scrolled
(scrolled-continuous Vs scrolled-doc are handled by different view
managers).

Returns: ???

Arguments

 * flow (string) - the flow to be set.


<h4 id="locations.getContents">getContents()</h4>

Get the Contents object of each rendered view.

Returns: (Contents[]) Array of Contents objects, one for each rendered
view.

Arguments:

 * none

<h4 id="locations.getRange">getRange(cfi, ignoreClass)</h4>

Get a Range from a Visible CFI.

Returns: (range) a range object.

Arguments:

 * cfi (string) - An EpubCFI string defining the range.
 * ignoreClass (string) - a class to be ignored???

<h4 id="locations.layout">layout()</h4>

Adjust the laout of the locations to reflowable or pre-paginated.

Returns: ???

Arguments:

 * settings (object) - ???


<h4 id="locations.moveTo">moveTo(offset)</h4>

Move the Rendition to a specific offset. Usually you would be better off
calling display().

Returns: ???

Arguments:

 * offset (object) - ???


<h4 id="locations.next">next()</h4>

Got to the next "page" in the locations.

Returns: (Promise) A Promise that resolves when the locations has been
updated to display the next "page".

Arguments:

 * none

<h4 id="locations.prev">prev()</h4>

Got to the previous "page" in the locations.

Returns: (Promise) A Promise that resolves when the locations has been
updated to display the previous "page".

Arguments:

 * none

<h4 id="locations.reportLocation">reportLocation()</h4>

Report the current location.

Returns: ???

Arguments:

 * none

<h4 id="locations.requireManager">requireManager(manager)</h4>

Require the manager from the passed string, or as a class function.

Returns: ???

Arguments

 * `manager` (string\|object) ???


<h4 id="locations.resize">resize([width], [height])</h4>

Trigger a resoze of the views.

Returns: ???

Arguments:

 * `width` (number) the width of the view.
 * `height` (number) the height of the view.

<h4 id="locations.setManager">setManager(manager)</h4>

Set the manager function.

Returns: ???

Arguments:

 * `manager` (function) set the manager function to the given function.

<h4 id="locations.spread">spread(spread, min)</h4>

Adjust if the locations uses spreads.

Returns: ???

Arguments:

 * spread (string) - 'none' or 'auto'.
 * min (int) - minimum width to use spreads at.

<h4 id="locations.start">start()</h4>

Start the rendering.

Returns: (Promise) a Promise that resolves when rendering has started.

Arguments:

 * none

<h4 id="locations.views">views()</h4>

Get the views member from the manager.

Returns: (Views)

Arguments:

 * none

