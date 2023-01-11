<h2 id="path">Path</h2>

The Path object provides methods for parsing and manipulating path strings.

This appears to be a wrapper for
[fchasen/path-webpack](https://github.com/fchasen/path-webpack).
It isn't obvious why this is used. One feature appears to be that 'cwd',
used for resolution of relative paths, is hard coded to '/'.


<h3 id="path.constructor">Constructor: new Path(pathString)</h3>

Constructs a new Path object instance.

```js
const path = new Path(pathString);
```
Arguments:
 
 * `pathString` (string) - a URL string (relative or absolute)

Returns: an instance of Path.


<h3 id='path.methods'>Methods</h3>


<h4 id="path.parse">parse(what)</h4>

Parse the path.

Arguments:

 * `what` - (string) a URL string (relative or absolute)

Returns: (object) - An object with properties for the various parts of the
path:

 * root - the root of the path. '/' on Posix systems. '<drive>:\\' on windows.
 * dir - the path, up to and excluding a final path separator or end of string.
 * base - the path following the dir
 * ext - If base includes a '.', the final '.' and what follows
 * name - base excluding the final ext

If `what` is a full URL (heuristic: if it includes '://') then the path
portion of the URL is used.

<h4 id="path.isAbsolute">isAbsolute(what)</h4>

Return true if the path is absolute.

Arguments:

 * what - (string) - the path to be tested. **Default**: this.path.

Returns: (boolean) - true iff the path is absolute.

<h4 id="path.isDirectory">isDirectory(what)</h4>

Check if what ends with directory separator ('/').

Arguments:

 * `what` - (string) - the path to be checked

Returns: (boolean) - true if what ends with a '/' character.

<h4 id="path.resolve">resolve(what)</h4>

Resolve an absolute path.

Arguments:

 * what - (string) The path to be resolved

Returns: (string) - what prefixed by this.directory if what is relative,
otherwise what.

<h4 id="path.relative">relative(what)</h4>

Resolve a path relative to the directory of the Path instance.

Arguments:

 * what - (string) The path to be resolved

Returns: (string) - a relative path to what, starting from this.directory.

If what includes '://', it is returned unmodified. So this only modifies
paths without scheme://host. 

<h4 id="path.splitPath">splitPath(filename)</h4>

This is not used and it looks like it will not work. It appears to be
dependent on the undefined this.splitPathRe.

<h4 id="path.toString">toString()</h4>

Returns this.path.

