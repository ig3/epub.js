<h2 id="container">Container</h2>

The Container object provides methods for parsing and accessing an EPUB
Container.

<h3 id="container.constructor">Constructor: new Container(containerString)</h3>

Constructs a new Container object instance.

```js
const container = new Container(document);
```
Arguments:
 
 * `document` (document) - a DOM document element for the parsed Container
   XML.

Returns: an instance of Container.


<h3 id='container.methods'>Methods</h3>


<h4 id="container.parse">parse(containerDocument)</h4>

'Parse' the Container XML.

Arguments:

 * containderDocument - (document) - DOM document element from the parsed
   Container XML.

Returns: undefined.

This method requires that the given DOM document contains a 'rootfile'
element. It throws a 'No RootFile Found' error if not.

Sets this.packagePath to the value of the 'full-path' attribute of the
'rootfile' element.

Sets this.directory to the directory part of this.packagePath.

Sets this.encoding to the xmlEncoding of the DOM document.

Note: this uses Document.xmlEncoding which is a deprecated attributed of
the DOM Document API. Maybe should use the characterSet or inputEncoding
property instead???

I don't think the encoding attribute is used anywhere. It appears to only
be used in Book / book.js, where only the packagePath attribute and destroy
methods are used.

<h4 id="container.destroy">destroy()</h4>
