---
layout: page
title: Guide to epub.js
menu: guide
lang: en
redirect_from: "/guide/guide.html"
---

# Guide

## EPUB

There are many formats for electronic books (e-books). See, for example,
the [Calibre](https://calibre-ebook.com/) application, with support for
over 40 file formats.

[EPUB](https://en.wikipedia.org/wiki/EPUB) is one family of standards for
e-books typically manifest as files with the extension '.epub'. There are
multiple versions of the standard from
[ISO/IEC](https://www.iso.org/standard/53255.html),
[W3C](https://www.w3.org/publishing/epub/epub-spec.html)
and maybe others.

There are multiple versions of the EPUB standards with versions 2 and 3
being most often referred to. These imply that there is a version 1
somewhere. 

There are other standards that include 'epub' in their name, including:

 * [EPUB Zero](https://dauwhe.github.io/epub-zero/)
 * [EPUB+WEB](https://w3c.github.io/epubweb/)
 * [Web Publications for the Open Web Platform](https://w3c.github.io/dpub-pwp/)

Of all this, it is the EPUB 3.2 standard (or 3.x - not sure) that is
relevant to epub.js.


### EPUB 3.2

[EPUB 3.2](https://www.w3.org/publishing/epub/epub-spec.html) is a
specification of the [W3C](https://www.w3.org/). Per the abstract of this
specification:

> EPUB® 3 defines a distribution and interchange format for digital publications and documents. The EPUB format provides a means of representing, packaging and encoding structured and semantically enhanced Web content — including HTML, CSS, SVG and other resources — for distribution in a single-file container. This specification represents the second major revision of the standard.

This specification is actually the root of a collection of specifications
which collectively specify the form, content, syntax and semantics of 
[EPUB Publications](https://www.w3.org/publishing/epub/epub-spec.html#dfn-epub-publication)
.

In order to understand what the
[@ig3/epub.js](https://github.com/ig3/epub.js) package does, it is
necessary to be familiar with this standard and its jargon. This package is
provides a JavaScript library for rendering EPUB Publications. In the
terminology of the of the specification, it is a library to facilitate
implementation of an
[EPUB Reading System](https://www.w3.org/publishing/epub/epub-spec.html#dfn-epub-reading-system).

Key terms and concepts include:

 * [EPUB Publication](https://www.w3.org/publishing/epub/epub-spec.html#dfn-epub-publication)
 * [EPUB Package](https://www.w3.org/publishing/epub/epub-spec.html#dfn-epub-package)
 * [EPUB Container](https://www.w3.org/publishing/epub/epub-spec.html#dfn-epub-container)

The EPUB Container is one, concrete manifestation of an EPUB Package as a
single ZIP archive file. If the contents of the ZIP archive are extracted,
collectively the extracted content still constitutes the EPUB Package.

## Building

### Tools

#### babel

Babel transpiles the code in the src directory to corresponding code in the
lib directory.

Targets are the last two version of:

 * Chrome
 * Safari
 * ChromeAndriod
 * iOS
 * Firefox
 * Edge

#### webpack

The distribution libraries are assembed by webpack.
