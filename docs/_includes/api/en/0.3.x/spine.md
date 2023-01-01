<h2 id="spine">Spine</h2>

The Spine object deals with spine of a book.

<h3 id="spine.constructor">Constructor: new Spine()</h3>

Constructs a new, empty Spine object.

```js
const spine = new Spine();
```
Arguments:

 * none 

Returns: an instance of Spine.

<h3 id='spine.methods'>Methods</h3>


<h4 id="spine.unpack">unpack(package, resolver, canonical)</h4>

Populate the Spine instance with the content of the spine element of the
opf of the book.

Returns: undefined.

Arguments:

 * package (Packaging) - a Packaging object derived from the opf of the
   book, including the spine.
 * resolver (function)
 * canonical (function) 

<h4 id="spine.get"> get([target])</h4>

Returns: (Section)  an item from the spine.

Arguments:

 * `target` (string\|number) identifier of the spine item.

If `target` is undefined, get the first 'linear' element of the spine is
returned or the last element if none prior are linear.

If `target` is a number, it is an index into the spine array.

If `target` is a string it may be an epubcfi, an ID prefixed by '#' or an
href value. The corresponding spine element is returned.

<h4 id="spine.parse">parse(contents, cfiBase, chars)</h4>

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

<h4 id="spine.attachTo">attachTo(element)</h4>

Attach the spine container to the given element in the DOM. The
container must be attached before the rendering can begin.

Returns: Promise that resolves when the container has been attached.

Arguments:

 * element (element) - The DOM element to which the container should be
   attached.

<h4 id="spine.clear">clear()</h4>

Clear the rendered views.

Returns: ???

Arguments:

 * none

<h4 id="spine.currentLocation">currentLocation()</h4>

Get the CurrentLocation object.

Returns: (displayedLocation\|Promise) The displayedLocation object with the
current location or a Promise that resolves to this.

Arguments:

 * none

<h4 id="spine.destroy">destroy()</h4>

Remove and Clean Up the Rendition.

Returns: ???

Arguments:

 * none

<h4 id="spine.direction">direction(direction)</h4>

Adjust the direction of the spine.

Returns: ???

Arguments:

 * direction (string) - the direction for the spine.

<h4 id="spine.display">display(target)</h4>

Display a point in the book.

The request will be added to the rendering Queue, so it will wait until the
book is opened, rendering started and all previously queued rendering tasks
have finished.

Returns: (Promise) a promise that resolves to ??? when the given target has
been displayed in the spine.

Arguments:

 * target (string) - URL, EpubCFI or floating point number in the range 0
   to 1, that determines the location in the book to be displayed.


<h4 id="spine.flow">flow(flow)</h4>

Adjust the flow of the spine to paginated or scrolled
(scrolled-continuous Vs scrolled-doc are handled by different view
managers).

Returns: ???

Arguments

 * flow (string) - the flow to be set.


<h4 id="spine.getContents">getContents()</h4>

Get the Contents object of each rendered view.

Returns: (Contents[]) Array of Contents objects, one for each rendered
view.

Arguments:

 * none

<h4 id="spine.getRange">getRange(cfi, ignoreClass)</h4>

Get a Range from a Visible CFI.

Returns: (range) a range object.

Arguments:

 * cfi (string) - An EpubCFI string defining the range.
 * ignoreClass (string) - a class to be ignored???

<h4 id="spine.layout">layout()</h4>

Adjust the laout of the spine to reflowable or pre-paginated.

Returns: ???

Arguments:

 * settings (object) - ???


<h4 id="spine.moveTo">moveTo(offset)</h4>

Move the Rendition to a specific offset. Usually you would be better off
calling display().

Returns: ???

Arguments:

 * offset (object) - ???


<h4 id="spine.next">next()</h4>

Got to the next "page" in the spine.

Returns: (Promise) A Promise that resolves when the spine has been
updated to display the next "page".

Arguments:

 * none

<h4 id="spine.prev">prev()</h4>

Got to the previous "page" in the spine.

Returns: (Promise) A Promise that resolves when the spine has been
updated to display the previous "page".

Arguments:

 * none

<h4 id="spine.reportLocation">reportLocation()</h4>

Report the current location.

Returns: ???

Arguments:

 * none

<h4 id="spine.requireManager">requireManager(manager)</h4>

Require the manager from the passed string, or as a class function.

Returns: ???

Arguments

 * `manager` (string\|object) ???


<h4 id="spine.resize">resize([width], [height])</h4>

Trigger a resoze of the views.

Returns: ???

Arguments:

 * `width` (number) the width of the view.
 * `height` (number) the height of the view.

<h4 id="spine.setManager">setManager(manager)</h4>

Set the manager function.

Returns: ???

Arguments:

 * `manager` (function) set the manager function to the given function.

<h4 id="spine.spread">spread(spread, min)</h4>

Adjust if the spine uses spreads.

Returns: ???

Arguments:

 * spread (string) - 'none' or 'auto'.
 * min (int) - minimum width to use spreads at.

<h4 id="spine.start">start()</h4>

Start the rendering.

Returns: (Promise) a Promise that resolves when rendering has started.

Arguments:

 * none

<h4 id="spine.views">views()</h4>

Get the views member from the manager.

Returns: (Views)

Arguments:

 * none

