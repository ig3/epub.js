<h2 id="archive">Archive</h2>

The Archive object provides methods for unzipping and getting content from
an Epub Archive (a.k.a. a zip file).

[test](http://google.com)

<h3 id="archive.constructor">Constructor: new Archive()</h3>

Constructs a new Archive object.

```js
const archive = new Archive();
```
Arguments:
 
 * none

Returns: an instance of Archive.

Requires that the JSZip global exists. This would typically be set by
loading the jszip.js or jszip.min.js libraries before loading epub.js. If
it is not available, construction of an Archive instance will fail with an
exception: JSZip lib not loaded.


<h3 id='archive.methods'>Methods</h3>


<h4 id="archive.checkRequirements">checkRequirements()</h4>

Creates a new JSZip instance or throws exception: 'JSZIP lib not loaded' if
the instance cannot be created (typically becuase global JSZip is not
defined).

<h4 id="archive.open">open(input, isBase64)</h4>

Open an archive.

Arguments:

 * input - (binary) - the archive data.
 * isBase64 - (boolean) The data (input) is based64 encoded if true

Performs a JSZip loadAsync of the input data, with option base64 set to
isBase64.

This reads the data, base64 decoding it if indicated.



<h4 id="archive.openUrl">openUrl(zipUrl, isBase64)</h4>

Load and open an archive from a URL.

Arguments:

 * zipUrl - (string) the URL to get the zip file from
 * isBase64 - (boolean) set to true if the returned data will be base64
   encoded.

Performs an HTTP GET request to zipUrl then performs a JSZip loadAsync of
the resulting data, with option base64 set to isBase64.


<h4 id="archive.request">request(url, type)</h4>

Request a url from the archive.

I think 'url' here is a misnomer. I think it is actually the path or name
of the file within the zip file.

Arguments:

 * url - (string) 'a url to request from the archive'
 * type - (string) the expected type of the result. **Default**: the
   extension of the given 'url'.

Returns a promise that resolves to the data of the file at url.

If type isn't specified, the extension of the filename in the path of `url`
is used.

If type is 'blob' then the promise resolves to a Blob object of the binary
data is returned. Otherwise it resolves to a string of the data.

If the type is 'json', the JSON text is parsed and the resulting object is
returned.

If the type is 'xml', 'opf' or 'ncx', the XML text is parsed as 'text/xml' by
@xmldom/xmldom and the resulting object is returned.

If the type is 'xhtml', the XML text is parsed as 'application/xhtml+xml'
by @xmldom/xmldom and the resulting object is returned.

If the type is 'html' or 'html', the text is parsed as 'text/html' by
@xmldom/xmldom and the resulting object is returned.

Otherwise, the text is returned as-is.


<h4 id="archive.handleResponse">handleResponse(response, type)</h4>

Handle the response from JSZip file request.

Arguments:

 * response - (any) the content of the file from JSZip
 * type - (string) the expected type of the file content

Returns the content of the response, parsed according to type.
Parse the text of the response according to type.

If the type is 'json', the JSON text is parsed and the resulting object is
returned.

If the type is 'xml', 'opf' or 'ncx', the XML text is parsed as 'text/xml' by
@xmldom/xmldom and the resulting object is returned.

If the type is 'xhtml', the XML text is parsed as 'application/xhtml+xml'
by @xmldom/xmldom and the resulting object is returned.

If the type is 'html' or 'html', the text is parsed as 'text/html' by
@xmldom/xmldom and the resulting object is returned.

Otherwise, the text is returned as-is.

<h4 id="archive.getBlob">getBlob(url, type)</h4>

Gets a Blob from the Archive by Url.

Arguments:
 
 * url - (string) The path of the file to get from the archive
 * type - (string) The expected type of the file contents

Returns a Promise that resolves to a Blob containing the content of the file.

Note: url is only a url in the sense that it is url decoded, so it may
contain non-ascii characters that are URL encoded.

<h4 id="archive.getText">getText(url, encoding)</h4>

Get a string from the Archive by Url.

Arguments:

 * url - (string) the path of the file to be retrieved

Returns a Promise that resolves to a string containing the content of the file.

<h4 id="archive.getBase64">getBase64(url, mimeType)</h4>

Get a base64 encoded result from the archive by Url.

Arguments:

 * url - (string) the path of the file in the archive
 * mimeType - (string) the expected MIME type of the file

Returns a promise that resolves to a base64 encoded data URL encoding of
the file content (i.e. 'data:' + mimeType + ';base64,' + file_data.

<h4 id="archive.createUrl">createUrl(url, options)</h4>

Gets the file data at the given url.

Arguments:

 * url - (string) a url
 * options - (object) options for the url creation

Returns a Promise that resolves to a base64 endoced data URL representation
of the file contents if options.base64 is truthy, otherwise a Blob
containing the file data.

If the result for the given url is found in urlCache, the cached result is
returned. Otherwise getBlob or getBase64 is performed on the given url,
according to options.base64, the result is cached in urlCache and the
result is returned.

The method appears to be somewhat misnamed. It may return a data URL but it
may also return a Blob.

<h4 id="archive.revokeUrl">revokeUrl(url)</h4>

If the URL has been cached, 'revoke' it via URL.revoekObjectURL().

<h4 id="archive.destroy">destroy()</h4>

Free resources. In particular, invoke URL.revokeObjectURL() on each object
in urlCache.

