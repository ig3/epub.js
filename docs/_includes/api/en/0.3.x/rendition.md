<h3 id="rendition">Rendition</h3>

The Rendition object encapsulates the rendering of an epub book. It has
methods for attaching the rendition to a DOM element, getting and setting
the location, etc.

<h4 id="rendition.constructor">Constructor: new Rendition(book, [options])</h4>

Constructs a new Rendition object for the rendition at the given Book.

```js
const rendition = new Rendition(book, [options]);
```
Arguments:
 
 * `book` (Book) - The instance of Book to be rendered.
 * `options` (object) - Optional options object to configure the rendition.

Returns: an instance of Rendition.

The `options` argument can have the following fields:

 * `width` (number) - The width of the rendered book.
 **Default**: undefined
 * `height` (number) - The height of the rendered book.
 **Default**: undefined
 * `ignoreClass` (string) - class for the cfi parser to ignore.
 **Default**: undefined
 * `manager` (string\|function\|object) - The manager to manage the
   rendition.
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


<h4 id='rendition.methods'>Methods</h4>


<h5 id="rendition.attachTo">attachTo(element)</h5>

Attach the rendition container to the given element in the DOM. The
container must be attached before the rendering can begin.

Returns: Promise that resolves when the container has been attached.

Arguments:

 * element (element) - The DOM element to which the container should be
   attached.

<h5 id="rendition.clear">clear()</h5>

Clear the rendered views.

Returns: ???

Arguments:

 * none

<h5 id="rendition.currentLocation">currentLocation()</h5>

Get the CurrentLocation object.

Returns: (displayedLocation\|Promise) The displayedLocation object with the
current location or a Promise that resolves to this.

Arguments:

 * none

<h5 id="rendition.destroy">destroy()</h5>

Remove and Clean Up the Rendition.

Returns: ???

Arguments:

 * none

<h5 id="rendition.direction">direction(direction)</h5>

Adjust the direction of the rendition.

Returns: ???

Arguments:

 * direction (string) - the direction for the rendition.

<h5 id="rendition.display">display(target)</h5>

Display a point in the book.

The request will be added to the rendering Queue, so it will wait until the
book is opened, rendering started and all previously queued rendering tasks
have finished.

Returns: (Promise) a promise that resolves to ??? when the given target has
been displayed in the rendition.

Arguments:

 * target (string) - URL or EpubCFI that determines the location in the
   book to be displayed.


<h5 id="rendition.flow">flow(flow)</h5>

Adjust the flow of the rendition to paginated or scrolled
(scrolled-continuous Vs scrolled-doc are handled by different view
managers).

Returns: ???

Arguments

 * flow (string) - the flow to be set.


<h5 id="rendition.getContents">getContents()</h5>

Get the Contents object of each rendered view.

Returns: (Contents[]) Array of Contents objects, one for each rendered
view.

Arguments:

 * none

<h5 id="rendition.getRange">getRange(cfi, ignoreClass)</h5>

Get a Range from a Visible CFI.

Returns: (range) a range object.

Arguments:

 * cfi (string) - An EpubCFI string defining the range.
 * ignoreClass (string) - a class to be ignored???

<h5 id="rendition.layout">layout()</h5>

Adjust the laout of the rendition to reflowable or pre-paginated.

Returns: ???

Arguments:

 * settings (object) - ???


<h5 id="rendition.moveTo">moveTo(offset)</h5>

Move the Rendition to a specific offset. Usually you would be better off
calling display().

Returns: ???

Arguments:

 * offset (object) - ???


<h5 id="rendition.next">next()</h5>

Got to the next "page" in the rendition.

Returns: (Promise) A Promise that resolves when the rendition has been
updated to display the next "page".

Arguments:

 * none

<h5 id="rendition.prev">prev()</h5>

Got to the previous "page" in the rendition.

Returns: (Promise) A Promise that resolves when the rendition has been
updated to display the previous "page".

Arguments:

 * none

<h5 id="rendition.reportLocation">reportLocation()</h5>

Report the current location.

Returns: ???

Arguments:

 * none

<h5 id="rendition.requireManager">requireManager(manager)</h5>

Require the manager from the passed string, or as a class function.

Returns: ???

Arguments

 * `manager` (string\|object) ???


<h5 id="rendition.resize">resize([width], [height])</h5>

Trigger a resoze of the views.

Returns: ???

Arguments:

 * `width` (number) the width of the view.
 * `height` (number) the height of the view.

<h5 id="rendition.setManager">setManager(manager)</h5>

Set the manager function.

Returns: ???

Arguments:

 * `manager` (function) set the manager function to the given function.

<h5 id="rendition.spread">spread(spread, min)</h5>

Adjust if the rendition uses spreads.

Returns: ???

Arguments:

 * spread (string) - 'none' or 'auto'.
 * min (int) - minimum width to use spreads at.

<h5 id="rendition.start">start()</h5>

Start the rendering.

Returns: (Promise) a Promise that resolves when rendering has started.

Arguments:

 * none

<h5 id="rendition.views">views()</h5>

Get the views member from the manager.

Returns: (Views)

Arguments:

 * none

