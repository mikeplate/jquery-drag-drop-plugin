Drag and Drop, jQuery Plugin
============================

Overview
--------

This is a jQuery plugin for handling drag and drop operations with transparent support for both mouse
and touch events. This means that you will be able to use the exact same code for desktop and mobile
web sites.

Usage
-----

Include the JavaScript file jquery.drag-drop.plugin.js in your html page.

~~~~ html
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.6.4/jquery.min.js"></script>
<script src="jquery.drag-drop.plugin.js"></script>
~~~~

The plugin is named "dragdrop" and can be applied to an element or a container of elements that should
be draggable. You will probably also specify some options while applying the plugin.

~~~~ javascript
$("#area").dragdrop();
$("#area").dragdrop({ makeClone: true, dragClass: "whileDragging"});
~~~~

Without any options, the default behaviour is to enable dragging of any elements inside the matched
elements when dragdrop() is called and to enable dropping on any element that has the CSS class
"drop" applied. But by using function callbacks like canDrag and canDrop, you can specify exactly
what can be dragged and where it can be dropped. And you can also specify what actually happens on
a drop with the function callback didDrop.

If you have an element containing many draggable elements, you can either attach the plugin to
each individual element inside the container or attach it to the single containing element and
then implement canDrag to make sure that the correct child of the container is dragged.

Options
-------

The plugin supports the following options when it is initialized for a source:

* __makeClone__ can be true or false. Default is false. If true, the actual source element won't be the
  element that is dragged but rather a clone of it.
* __sourceClass__ can be the name of a CSS class. This class is applied to the source element
  in its original position (if visible) while it is dragged.
* __sourceHide__ can be true or false. When true, the original element is set to invisible while the
  dragging occurs.
* __dragClass__ can be the name of a CSS class. If specified, it is applied to the element that is
  being dragged while the drag operation is active. Note that if makeClone is false, this is also
  the actual source element.
* __canDropClass__ can be the name of a CSS class. If specified, will be applied to the droppable
  area element whenever a dragged element is hovering over it, to signify that the user can drop
  at this time.
* __dropClass__ can be the name of a CSS class. This class name is used to identify droppable
  area elements. The default is "drop". If a callback function is specified under "canDrop", this
  class name has no effect.
* __container__ can be a jQuery element of a container. If specified, elements dragged will not be able
  to move outside of that container.
* __canDrag__ can be a callback function that returns true or false. You can use this callback if you'd
  like to apply the plugin to a larger container, and then only make specific elements inside that
  container draggable by returning true from the callback if you've determined the current element
  as eligable for dragging.
* __canDrop__ can be a callback function that returns true or false. Return true if the dragged element
  can be dropped on the specified element. If this function is used, the "dropClass" setting has
  no effect.
* __didDrop__ can be a callback function. If specified, it is assumed to take care of all operations
  and effects to occur after a successful drag and drop has been performed. Otherwise, the default
  operation is to restore the class on the source element and if makeClone is false the
  element will be appended as a child to the droppable element.

License
-------

This software is released under the [MIT License](https://github.com/mikeplate/jquery-drag-drop-plugin/blob/master/LICENSE.txt).

