---
layout: home
title: epub.js - a JavaScript library for rendering EPUB 3 Publications
menu: home
lang: en
---
<section id="home-content">
  {% include header/header-{{ page.lang }}.html %}
  <div id="overlay"></div>
  <div id="homepage-leftpane" class="pane">
    <section id="description">
        <div class="express"><a href="{{ site.baseurl }}/">@ig3/epub.js</a></div>
        <span class="description">A library for rendering <a href="https://en.wikipedia.org/wiki/EPUB">EPUB 3</a> documents in the browser.</span>
    </section>
  </div>
</section>
<section id="announcements">
  {% include announcement/announcement-en.md %}
</section>

<section id="intro">
  <div>
  The @ig3/epub.js package provides a library for rendering EPUB 3
  Publications in the browser. It provides objects and methods for
  downloding, rendering and navigating through the publications. It is a
  basis for building browser based EPUB Readers.
  </div>
  <div>
  The @ig3/epub.js library supports publications conforming to the the current
  <a href="https://www.w3.org/publishing/epub/epub-spec.html">EPUB 3.2</a>
  specifications. But comments in the code suggest that it may also support
  publications conforming to th3 EPUB 2 specifications. 
  </div>

</section>
