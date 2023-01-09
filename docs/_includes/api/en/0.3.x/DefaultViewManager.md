<h2 id="DefaultViewManager">DefaultViewManager</h2>

The default view provides a  paginated view with support for vertical or
horizontal scrolling and left-to-right or right-to-left presentation of
horizontal scrolling.

```js
const manager = new DefaultViewManager(options);
```

Options:
 * view
 * queue
 * request
 * settings

<h3 id='DefaultViewManager.events'>Events</h3>

DefaultViewManager is an event emitter. It emits the following events:

 * orientationchange
 * resized
 * added
 * resize
 * scroll
 * scrolled
 * removed

But I don't see evidence that the removed event is actually emitted. The
constant is defined and the Rendition instance listens for the event, but I
don't think it is emitted. At least, I can't see where it is emitted.

<h3 id='DefaultViewManager.methods'>Methods</h3>

<h4 id="DefaultViewManager.render">render(element, size)</h4>

The view is full size if the element to render to is the html of body
element. For full size view, overflow is visible.

Creates a new Stage (is this an element within the element rendered to?) It
seems so, after being created, it is attached to `element`.


<h4 id="DefaultViewManager.addEventListeners">addEventListeners()</h4>

Called from the constructor.

A listener is added for the 'unload' event on `window`. When this event is
received, the DefaultViewManager instance is destroyed.

A listener is added for the scroll event on the container (the `window` if
display is full screeen, otherwise the container element).


<h4 id="DefaultViewManager.removeEventListeners">removeEventListeners()</h4>

Called from the destroy method.

This removes the listener on the container for the scroll event but it
doesn't remove the listener on the window for the unload event. The
omission of the latter is probably a bug.

<h4 id="DefaultViewManager.destroy">destroy()</h4>

Called from the unload event handler on `window`.

Frees resources, clears timers, destroys related objects, etc.

<h4 id="DefaultViewManager.onOrientationChange">onOrientationChange(e)</h4>

It isn't obvious if or when this is called. It looks like an event handler,
based on the argument list.

This calls the resize method.

The call is deferred for 500ms delay to accomodate a fault / feature of IOS
10.3. 

Emits the orientationchange event.

<h4 id="DefaultViewManager.resized">onResized(e)</h4>

This looks like an event handler, based on the argument list. It is passed
to the onResize method of the stage which, I presume, calls it.

The event is ignored.

Calls the resize method without arguments.

<h4 id="DefaultViewManager.resize">resize(width, height, epubcfi)</h4>

Gets the size of the stage from the stage object.

If the size hasn't changed, does nothing else.

Otherwise, current views are cleared, the layout is updated (see
updateLayout method) and the resized event is emitted.

<h4 id="DefaultViewManager.createView">createView(section, forceRight)</h4>

Returns a new View object.

<h4 id="DefaultViewManager.handleNextPrePaginated">handleNextPrePaginated(forceRight, section, action)</h4>

Some special handling for pre-paginated content. I don't know anything
about pre-paginated content. This is a bit mysterious.

<h4 id="DefaultViewManager.display">display(section, target)</h4>

Display the content of the given section in the element `target`.

Target identifies the location in the section to be displayed. The display
is moved to this location.

<h4 id="DefaultViewManager.afterDisplayed">afterDisplayed(view)</h4>

Emits the added event.

<h4 id="DefaultViewManager.afterResized">afterResized(view)</h4>

Emits the resize event.

<h4 id="DefaultViewManager.moveTo">moveTo(offset, width)</h4>

Move the displayed part of the section to the given offset

<h4 id="DefaultViewManager.add">add(section, forceRight)</h4>

Add a section.

<h4 id="DefaultViewManager.append">append(section, forceRight)</h4>
<h4 id="DefaultViewManager.prepend">prepend(section, forceRight)</h4>
<h4 id="DefaultViewManager.counter">counter(bounds)</h4>
<h4 id="DefaultViewManager.next">next()</h4>
<h4 id="DefaultViewManager.prev">prev()</h4>
<h4 id="DefaultViewManager.current">current()</h4>
<h4 id="DefaultViewManager.clear">clear()</h4>
<h4 id="DefaultViewManager.currentLocation">currentLocation()</h4>
<h4 id="DefaultViewManager.scrolledLocation">scrolledLocation()</h4>
<h4 id="DefaultViewManager.paginatedLocation">paginatedLocation()</h4>
<h4 id="DefaultViewManager.isVisible">isVisible(view, offsetPrev, offsetNext, _container)</h4>
<h4 id="DefaultViewManager.visible">visible()</h4>
<h4 id="DefaultViewManager.scrollBy">scrollBy(x, y, silent)</h4>
<h4 id="DefaultViewManager.scrollTo">scrollTo(x, y, silent)</h4>
<h4 id="DefaultViewManager.onScroll">onScroll()</h4>
<h4 id="DefaultViewManager.bounds">bounds()</h4>
<h4 id="DefaultViewManager.applyLayout">applyLayout(layout)</h4>
<h4 id="DefaultViewManager.updateLayout">updateLayout()</h4>
<h4 id="DefaultViewManager.setLayout">setLayout(layout)</h4>
<h4 id="DefaultViewManager.updateWritingMode">updateWritingMode(mode)</h4>
<h4 id="DefaultViewManager.updateAxis">updateAxis(axis, forceUpdate)</h4>
<h4 id="DefaultViewManager.updateFlow">updateFlow(flow, defaultScrolledOverflow)</h4>
<h4 id="DefaultViewManager.getContents">getContents()</h4>
<h4 id="DefaultViewManager.direction">direction(dir)</h4>
<h4 id="DefaultViewManager.isRendered">isRendered()</h4>
