<ul>
  <li>
    <p class="announcement-title">@ig3/epub.js forked December 2022.</p>
    <p markdown="1">
     [@ig3/epub.js](https://github.com/ig3/epub.js) was forked from
     [futurepress/epub.js](https://github.com/futurepress/epub.js)
     December 2022, to implement a minor enhancement and to add this
     documentation.
    </p>
    <p markdown="1">
     I maintain this purely for my own use and you almost
     certainly should be using the original implementation by futurepress:
     [futurepress/epub.js](https://github.com/futurepress/epub.js).
    </p>
    <p markdown="1">
     If you are reading texts with few space characters (Chinese in my
     case) then this fork might be of some interest to you. It uses an
     algorithm not dependent on frequent space characters (as are common in
     English and other Latin texts) to generate epubcfi at page boundaries.
     This improves resolution of the generated epubcfis so that page
     reloading doesn't cause page changes and avoids pages being skipped at
     the end of chapters by 'next' navigation.
    </p>
    <p markdown="1">
     Similarly this documentation is for my own use, as I try to understand
     how epub.js works well enough to fix the problems I have encountered.
     It is not authoritative and far from complete. As I don't understand
     how epub.js works, it probably has many errors.
    </p>
  </li>
</ul>
