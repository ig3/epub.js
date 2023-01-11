<h2 id="packaging">Packaging</h2>

The Packaging object consititutes an Open Packaging Format parser.

The Open Packaging Format may be that described in
[EPUB Packages 3.2](https://www.w3.org/publishing/epub/epub-packages.html#sec-package-doc)
as 'Package Document' though the code / comments / documentation doesn't
specify. This 'Package Document' specification is of an XML file with
extension '.opf', which seems consistent with the code but there are other
users of 'opf', including in EPUB 2.

<h3 id="packaging.constructor">Constructor: new Packaging([packageDocument])</h3>

Constructs a new Packaging object instance.

```js
const packaging = new Packaging();
```
Arguments:
 
 * `packageDocument` (document) - A DOM element - packageDocument OPF XML

Returns: an instance of Packaging.

The optional packageDocument may be as specified by:
[EPUB Packages 3.2](https://www.w3.org/publishing/epub/epub-packages.html#sec-package-doc)
as 'Package Document'.

The packageDocument is actually a DOM element. For example, it may be the
root element that results from parsing the Package Document (an XML
document) with DOMParser or @xmldom/xmldom.

<h3 id='packaging.methods'>Methods</h3>


<h4 id="packaging.parse">parse(packageDocument)</h4>

Parse an
[EPUB 3 Package Document](https://www.w3.org/publishing/epub/epub-packages.html#sec-package-doc) rendered as a DOM tree.

Arguments: 

 * packageDocument - (document) - a DOM document object resulting from
   loading / parsing an EPUB 3 Package Document.

Returns: (object) - An object containing the relevant data from the Package
Document:

 * metadata
 * spine
 * manifest
 * navPath
 * ncxPath
 * coverPath
 * spineNodeIndex

The Package Document should first be parsed to a DOM tree. The document
object of the resulting DOM tree should be passed to this method for
'parsing'.

Throws error:

 * 'Package File Not Found' - if packageDocument is falsy
 * 'No Metadata Found' - if the DOM tree does not contain a 'metadata'
   element.
 * 'No Manifest Found' - if the DOM tree does not contain a 'manifest'
   element.
 * 'No Spine Found' - if the DOM tree does not contain a 'spine' element.

<h4 id="packaging.parseMetadata">parseMetadata(xml)</h4>

'Parse' the 'metadata' node of the DOM tree representation of the EPUB 3
Package Document.

Arguments:

 * xml - (node) The 'metadata' DOM node of the parsed Package Document.

Returns: (object) - with properties:

 * title
 * creator
 * description
 * pubdate
 * publisher
 * identifier
 * language
 * rights
 * modified_date (from property dcterms:modified)
 * layout (from property rendition:layout)
 * orientation (from property rendition:orientation)
 * flow (from property rendition:flow)
 * viewport (from property rendition:viewport)
 * media_active_class (from property media:active-class)
 * spread (from property rendition:spread)

<h4 id="packaging.parseManifest">parseManifest(manifestXml)</h4>

'Parse' the 'manifest' node of the DOM tree representation of the EPUB 3
Package Document.

Arguments:

 * manifestXml - (node) - the 'manifest' DOM node of the parsed Package
   Document.

Returns: (object) - Keyed by the IDs of the manifest with values being
objects with properties:

 * href (from attribute href)
 * type (from attribute media-type)
 * overlay (from attribute media-overlay)
 * properties (from attribute properties)

Note: properties is an array formed by splitting the value of the
properties attribute on whitespace.

<h4 id="packaging.parseSpine">parseSpine(spineXml, manifest)</h4>
<h4 id="packaging.findUniqueIdentifier">findUniqueIdentifier(packageXml)</h4>
<h4 id="packaging.findNavPath">findNavPath(manifestNode)</h4>
<h4 id="packaging.findNcxPath">findNcxPath(manifestNode, spineNode)</h4>
<h4 id="packaging.findCoverPath">findCoverPath(packageXml)</h4>
<h4 id="packaging.getElement">getElement(xml, tag)</h4>
<h4 id="packaging.getPropertyText">getPropertyText(xml, property)</h4>
<h4 id="packaging.load">load(json)</h4>

Load JSON Manifest.

It is not clear what the format or purpose of this Manifest is.

It may be a
[Readium Web Publication Manifest](https://readium.org/webpub-manifest/)

But another possibility is a
[W3C Publication Manifest](https://www.w3.org/TR/pub-manifest/) which is
another JSON document that describes an electronic publication.

The properties of the JSON object accessed by the code seem consistent with
the former. 

Assuming it is the Readium Web Publication Manifest, this suggests that
epub.js has (at least vestigates of) support for
[Readium Packaging Format](https://readium.org/webpub-manifest/packaging.html).

See [this comment by fchasen](https://github.com/w3c/wpub/issues/119#issuecomment-357054182)

Arguments:

 * json - (object) The parsed JSON of the Manifest document

The argument name is misleading. It suggests that the value is JSON text
but it is not. The value must be an object. It may have been parsed from
JSON text at some point, but that is irrelevant to the load method.

The input object might have the following properties:
 * metadata - presumably an object
 * readingOrder - array of ???
 * spine - array of ???
 * resources - array of objects with properties including rel and href
 * toc - arry of objects with properties including title

Any other properties will be ignored. 
Returns: (object) And object with properties:

 * metadata
 * spine
 * manifest
 * navPath
 * ncxPath
 * coverPath
 * spineNodeIndex
 * toc

The values of these are references to the correspondingly named properties
of the Packaging instance. The actual values will be as extracted from the
Manifest document.

There is no validation of the input. Given that this method is used to
process data from external sources, the lack of validation is problematic.
Invalid data is likely to lead to failures elsewhere in the code with the
root cause not being obvious.

<h4 id="packaging.destroy">destroy()</h4>

