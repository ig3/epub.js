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

