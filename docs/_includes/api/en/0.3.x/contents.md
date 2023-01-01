<h2 id="contents">Contents</h2>

The Contents object handles DOM manipulation, queries and events for View
contents. The contents are typically the content of a chapter of the book.

<h3 id="contents.constructor">Constructor: new Contents(doc, content, cfiBase, sectionIndex)</h3>

Constructs a new Contents object for the content of the section (a.k.a.
chapter) of the given chapter of the book. The cfiBase and sectionIndex
must correspond to the given content, according to the spine of the book.

TODO: it would be better to pass a 'Section' object that encapsulated the
content, cfiBase and sectionIndex in a way that helps ensure they are
consistent.

```js
const contents = new Contents(doc, content, cfiBase, sectionIndex);
```
Arguments:
 
 * `doc` (???) - And object with documentElement and defaultView properties.
 * `content` (???) - ???. **Default**: doc.body.
 * `cfiBase` (???) - ???. **Default**: ''
 * `sectionIndex` (number) - integer index into the spine of the book that
   contains / refers to the given content. **Default**: 0

Returns: an instance of Contents.

<h3 id='contents.methods'>Methods</h3>

<h4>contentHeight(height)</h4>

Get or set the height of the content element or, if that is not set, the
body of the content document.

Returns: (number) - the height of the computed style of the window
(presumably containing the content - why not the height of the content
itself???) as integer number of pixels.

Arguments:

 * `height` (number\|string) - the height to be set on the content element.

`height` is either an integer number of pixels or a string compatible with
the height style of the content element.

The height of the content element is set if parameter `height` is truthy.
Therefore, the height cannot be set to 0.

The height of the window is always returned. But, which window??? Presumably
the window of the iframe presenting the content.


<h4>contentWidth(width)</h4>

Get or set the width of the content element or, if that is not set, the
body of the content document.

Returns: (number) - the width of the computed style of the window
(presumably containing the content - why not the width of the content
itself???) as integer number of pixels.

Arguments:

 * `width` (number\|string) - the width to be set on the content element.

`width` is either an integer number of pixels or a string compatible with
the width style of the content element.

The width of the content element is set if parameter `width` is truthy.
Therefore, the width cannot be set to 0.

The width of the window is always returned. But, which window??? Presumably
the window of the iframe presenting the content.

<h4 id="contents.listenedEvents">listenedEvents()</h4>

Get the DOM events that are listened for.

<h4>height(height)</h4>

Get or set the height of the content.

Returns: (number) the height of the computed style of the iframe element.

Arguments:

 * `height` (number\|string) - the height to be set on the iframe element.

`height` is an integer number of pixels or a string compatible with the
height style of the iframe.

<h4>locationOf(target, ignoreClass)</h4>

Get the location offset of the epubcfi or #id.

Returns: ({ left: (number), top: (number)}) - the left and top offsets of
the content specified by the epubcfi or #ID.

Arguments:

 * `target` (string) - the epubcfi or #id of the content to be located.
 * `ignoreClass` (???) - ???

If there is no document, { left: 0, top: 0 } is returned.

`target` must be either an epubcfi string or an ID prefixed by '#'

If `target` is an ID then it is the ID of an element in the DOM of the
content document.

<h4>overflow(overflow)</h4>

Gets or sets the overflow css style of the content (i.e. documentElement).

Returns: (string) the value of the overflow property of the computed style
of the documentElement.

Arguments:

 * `overflow` (string) - the value to set the overflow property of
   the computed style of the documentElement.

If `overflow` is truthy, the overflow property of the computed style of the
documentElement is set to it.

The value of the overflow property of the computed style of the
documentElement is always returned.

<h4>scrollHeight</h4>

Gets the scroll height of the documentElement, in pixels.

<h4>scrollWidth</h4>

Gets the scroll width of the documentElement, in pixels.

<h4>textHeight()</h4>

Get the height of the text using Range.

Returns: (number) the height of the bounding client rectanble of the range
containing all the content, plus the height of any border, in pixels.

Arguments:

 * none

This creates a range (document.createRange), sets the range to the contents
of the content node (DOM node, presumably) then gets the bounding client
rectangle of the selection and, if there is a border with height, adds the
height of the border.

<h4>textWidth()</h4>

Get the width of the text using Range.

Returns: (number) the width of the bounding client rectanble of the range
containing all the content, plus the width of any border, in pixels.

Arguments:

 * none

This creates a range (document.createRange), sets the range to the contents
of the content node (DOM node, presumably) then gets the bounding client
rectangle of the selection and, if there is a border with width, adds the
width of the border.

<h4>width(width)</h4>

Get or set the width of the content.

Returns: (number) the width of the computed style of the iframe element.

Arguments:

 * width (number\|string) - the width to be set on the iframe element.

The width is an integer number of pixels or a string compatible with the
width style of the iframe.

If width is truthy, the width of the iframe is set.

The width of the iframe is always returned.
