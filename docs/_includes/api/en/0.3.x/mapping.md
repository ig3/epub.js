<h3 id="mapping">Mapping</h3>

The Mapping object maps text locations to EpubCFI ranges.

<h4 id="mapping.constructor">Constructor: new Mapping(layout, direction,
axis, dev)<h4>

Constructs a new Mapping object.

```js
const mapping = new Mapping(layout, direction, axis, dev);
```
Arguments:
 
 * `layout` (Layout) - layout Layout to apply
 * `direction` (string) - Text direction - 'ltr' or 'rtl'. **Default**: 'ltr'
 * `axis` (string) - 'vertial' or 'horizontal'. **Default**: 'horizontal'
 * `dev` (boolean) - toggle developer highlighting. **Default**: false

Returns: an instance of Mapping.

<h4 id='mapping.methods'>Methods</h4>

<h5 id="mapping.findStart">findStart(root, start, end)</h5>

Find the Range that covers the start of the page.

Returns: (Range) - the range that covers the start of the page.

Arguments:

 * `root` (Node) - root node.
 * `start` (number) - offset of the start of the page.
 * `end` (number) - offset of the end of the page.

Check each text node within the root node and return the range of the first
node that begins within the bounds of the page or ends within or after the
page.

This assumes that the order that the walk() function walks the text nodes
is from left to right or top to bottom, according to axis. This may be true
of simple documents but might not be true of documents with positioned
elements.

<h5 id="mapping.page">page(contents, cfiBase, start, end)</h5>

Find the EpubCFI for the start and end of a page.

Returns: ({ start: (EpubCFI), end: (EpubCFI) }) - an object containing the
EpubCFI string of the start and end of the page.

Arguments:

 * `contents` (element) - the DOM element containing the contents of the
   section.
 * `cfiBase` (string) - the base of the EpubCFI that identifies the
   section.
 * `start` (number) - offset of the start of the page in pixels.
 * `end` (number) - offset of the end of the page in pixels.

`start` and `end` are horizontal or vertical offsets according to the axis
of the mapping (see constructor).

The content of the section is rendered in its entirety, split into pages by
CSS styling. Each page is at an offset from the start of the content:
vertical or horizontal, according to the axis.

<h5 id="mapping.section">section(view)</h5>

Find CFI pairs for entire section at once.

Returns: (EpubCFI[]) array of EpubCFI value for all the ranges in the
section.

Arguments:

 * `view` (View) - the view of the section.

