<ul>
  <li>
    <p class="announcement-title">@ig3/epub.js forked December 2022.</p>
    <p markdown="1">
     [@ig3/epub.js](https://github.com/ig3/epub.js) was forked from
     [futurepress/epub.js](https://github.com/futurepress/epub.js)
     December 2022, to implement a minor enhancement and to add this
     documentation. I maintain this purely for my own use and you almost
     certainly should be using the original implementation by futurepress:
     [futurepress/epub.js](https://github.com/futurepress/epub.js).

     If you are reading texts with few space characters (Chinese in my
     case) then this fork might be of some interest to you. Without space
     characters, the epubcfi values produced are at large intervals,
     sometimes whole chapters have no division. This causes navigation
     problems including page jumps when reloading at a location based on
     epubcfi and the next function skipping pages at the end of sections.

     Similarly the documentation is for my own benefit, as I try to
     understand how epub.js works well enough to fix the problems I have
     encountered. It is not authoritative and far from complete.

    </p>
  </li>
</ul>
