---
layout: home
title: epub.js - a JavaScript library for rendering ePub documents
menu: home
lang: en
---
<section id="home-content">
  {% include header/header-{{ page.lang }}.html %}
  <div id="overlay"></div>
  <div id="homepage-leftpane" class="pane">
    <section id="description">
        <div class="express"><a href="/">Express</a><a href="{{ page.lang }}/changelog/4x.html#{{ site.data.express.current_version }}" id="express-version">{{ site.data.express.current_version }}</a></div>
        <span class="description">Fast, unopinionated, minimalist web framework for <a href='https://nodejs.org/en/'>Node.js</a></span>
    </section>
    <div id="install-command">$ npm install express --save</div>
  </div>
</section>
<section id="announcements">
  {% include announcement/announcement-en.md %}
</section>

<section id="intro">

  <div id="boxes" class="clearfix">
    <div id="web-applications">
      <h3>ePub Applications</h3> epub.js is a JavaScript library for
      rendering [ePub](https://en.wikipedia.org/wiki/EPUB) documents
      in the browser. It is a basis for building browser based ePub
      reader applications.
    </div>

    <div id="apis">
      <h3>APIs</h3> epub.js provides simple APIs for loading, rendering and
      navigating ePub documents.
    </div>

  </div>

</section>
