### CSS Box Model
![Box Model](http://tutorials.jenkov.com/images/css/box-model.png)

[CSS Cheat Sheet](http://websitesetup.org/wp-content/uploads/2014/09/CSS3_CHEAT_SHEET_PDF.pdf)

### CSS Positioning Vocab
- static - Normal document flow. (Default if no positioning is defined)
- relative - Relative to normal document flow.
- absolute - The element is taken out of the normal document flow and shown at the location specified by the CSS left and top attribute(or right and bottom).
- fixed - Fixed position on the screen regardless of scrolling. (Not supported by Internet Explorer)


## CSS Positioning Walkthrough
### Pulled from [CSS Positioning in 10 Steps](http://www.barelyfitz.com/screencast/html-training/css/positioning/
)


## 1. position:static
The default positioning for all elements is position:static, which means the element is not positioned and occurs where it normally would in the document.

Normally you wouldn't specify this unless you needed to override a positioning that had been previously set.
```
.div-1 {
 position:static;
}
```


## 2. position:relative
If you specify position:relative, then you can use top or bottom, and left or right to move the element relative to where it would normally occur in the document.

Let's move div-1 down 20 pixels, and to the left 40 pixels:
```
.div-1 {
 position:relative;
 top:20px;
 left:-40px;
}
```
Notice the space where div-1 normally would have been if we had not moved it: now it is an empty space. The next element (div-after) did not move when we moved div-1. That's because div-1 still occupies that original space in the document, even though we have moved it.

It appears that position:relative is not very useful, but it will perform an important task later in this tutorial


## 3. position:absolute
When you specify position:absolute, the element is removed from the document and placed exactly where you tell it to go.

Let's move div-1a to the top right of the page:
```
.div-1a {
 position:absolute;
 top:0;
 right:0;
}
```
Notice that this time, since div-1a was removed from the document, the other elements on the page were positioned differently: div-1b, div-1c, and div-after moved up since div-1a was no longer there.

Also notice that div-1a was positioned in the top right corner of the page. It's nice to be able to position things directly the page, but it's of limited value.

What I really want is to position div-1a relative to div-1. And that's where relative position comes back into play


## 4. position:relative + position:absolute
If we set relative positioning on div-1, any elements within div-1 will be positioned relative to div-1. Then if we set absolute positioning on div-1a, we can move it to the top right of div-1:

```
.div-1 {
 position:relative;
}
.div-1a {
 position:absolute;
 top:0;
 right:0;
}
```

## 5. two column absolute
Now we can make a two-column layout using relative and absolute positioning!
```
.div-1 {
 position:relative;
}
.div-1a {
 position:absolute;
 top:0;
 right:0;
}
.div-1b {
 position:absolute;
 top:0;
 left:0;
}
```
One advantage to using absolute positioning is that we can position the elements in any order on the page, regardless of the order they appear in the HTML. So I put div-1b before div-1a.

Take note: Other elements are being obscured by the absolutely positioned elements.


## 6. two column absolute height
One solution to covered elements is to set a fixed height on the elements.

But that is not a viable solution for most designs, because we usually do not know how much text will be in the elements, or the exact font sizes that will be used.
```
.div-1 {
 position:relative;
 height:250px;
}
.div-1a {
 position:absolute;
 top:0;
 right:0;
}
.div-1b {
 position:absolute;
 top:0;
 left:0;
}
```


## 7. Floats
For variable height columns, absolute positioning does not work, so let's come up with another solution.

We can "float" an element to push it as far as possible to the right or to the left, and allow text to wrap around it. This is typically used for images, but we will use it for more complex layout tasks (because it's the only tool we have).
```
.div-1a {
 float:left;
}
```


## 8. float columns
If we float one column to the left, then also float the second column to the left, they will push up against each other.
```
.div-1a {
 float:left;
}
.div-1b {
 float:left;
}
```


## 9. float columns with clear
Then after the floating elements we can "clear" the floats to push down the rest of the content.
```
.div-1a {
 float:left;
}
.div-1b {
 float:left;
}
.div-1c {
 clear:both;
}
```
