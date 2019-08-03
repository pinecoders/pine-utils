![PineCoders](/images/PineCodersLong.png "PineCoders")

# Function to draw a rectangle on chart.

#### Description:

Function that draws a rectangle.

##### References:
* [noreference](/ "No Reference.")


#### Code:

<details open>
  <!-- leave a blank line after summary -->
  <summary>@version=4</summary>

```javascript
//  ||─────────────────────────────────────────────────────────────────────────||
//  ||  Draw a rectangle with 2 vector2D(x, y) coordinates:
//  ||─────────────────────────────────────────────────────────────────────────||
//  |{─────────────────────────────────────────────────────────────────────────||
//  ||  Parameters:
//  ||      _x1, _y1    (series )   : first vector2D(x, y) coordinates.
//  ||      _x2, _y2    (series )   : second vector2D(x, y) coordinates.
//  ||      _xloc       (string )   : options: xloc.bar_index and xloc.bar_time. 
//  ||      _extend     (string )   : options: extend.none, extend.right, extend.left, extend.both
//  ||      _color      (color  )   : color code ex:. #000000, color.black, color.new(#000000, 40)
//  ||      _style      (string )   : options: : line.style_solid, line.style_dotted, line.style_dashed, line.style_arrow_left, line.style_arrow_right, line.style_arrow_both
//  ||      _width      (integer)   : width in pixels.
f_line_rectangle(_x1, _y1, _x2, _y2, _xloc, _extend, _color, _style, _width)=>
    //    (x1,y2) Side2 (x2, y2)
    //          ┌───────┐
    //          │       │
    //   Side1  │       │ Side3
    //          │       │
    //          └───────┘
    //    (x1,y1) Side4 (x2, y1)
    var line _side1 = na
    var line _side2 = na
    var line _side3 = na
    var line _side4 = na
    //  clear previous lines:
    line.delete(_side1)
    line.delete(_side2)
    line.delete(_side3)
    line.delete(_side4)
        
    //  draw the lines:
    _side1 := line.new(
         x1 = _x1, y1 = _y1, 
         x2 = _x1, y2 = _y2, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side2 := line.new(
         x1 = _x1, y1 = _y2, 
         x2 = _x2, y2 = _y2, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side3 := line.new(
         x1 = _x2, y1 = _y2, 
         x2 = _x2, y2 = _y1, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side4 := line.new(
         x1 = _x2, y1 = _y1, 
         x2 = _x1, y2 = _y1, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
//  ||─────────────────────────────────────────────────────────────────────────||

```
</details>


#### Example:

Draws a  rectangle on chart.<br/>

<details open>
  <!-- leave a blank line after summary -->
  <summary>Example Code</summary>

<!--  -->
<!-- code goes between the backticks: -->
```javascript
//@version=4
study(title="[RS]Function - Geometric Line Drawings")
//  ||─────────────────────────────────────────────────────────────────────────||
//  ||  Draw a rectangle with 2 vector2D(x, y) coordinates:
//  ||─────────────────────────────────────────────────────────────────────────||
//  |{─────────────────────────────────────────────────────────────────────────||
//  ||  Parameters:
//  ||      _x1, _y1    (series )   : first vector2D(x, y) coordinates.
//  ||      _x2, _y2    (series )   : second vector2D(x, y) coordinates.
//  ||      _xloc       (string )   : options: xloc.bar_index and xloc.bar_time. 
//  ||      _extend     (string )   : options: extend.none, extend.right, extend.left, extend.both
//  ||      _color      (color  )   : color code ex:. #000000, color.black, color.new(#000000, 40)
//  ||      _style      (string )   : options: : line.style_solid, line.style_dotted, line.style_dashed, line.style_arrow_left, line.style_arrow_right, line.style_arrow_both
//  ||      _width      (integer)   : width in pixels.
f_line_rectangle(_x1, _y1, _x2, _y2, _xloc, _extend, _color, _style, _width)=>
    //    (x1,y2) Side2 (x2, y2)
    //          ┌───────┐
    //          │       │
    //   Side1  │       │ Side3
    //          │       │
    //          └───────┘
    //    (x1,y1) Side4 (x2, y1)
    var line _side1 = na
    var line _side2 = na
    var line _side3 = na
    var line _side4 = na
    //  clear previous lines:
    line.delete(_side1)
    line.delete(_side2)
    line.delete(_side3)
    line.delete(_side4)
        
    //  draw the lines:
    _side1 := line.new(
         x1 = _x1, y1 = _y1, 
         x2 = _x1, y2 = _y2, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side2 := line.new(
         x1 = _x1, y1 = _y2, 
         x2 = _x2, y2 = _y2, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side3 := line.new(
         x1 = _x2, y1 = _y2, 
         x2 = _x2, y2 = _y1, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side4 := line.new(
         x1 = _x2, y1 = _y1, 
         x2 = _x1, y2 = _y1, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
//  ||─────────────────────────────────────────────────────────────────────────||
//  ||  Example:
show_rectangle = input(true)
rect_x1 = input(defval=10)
rect_y1 = input(defval=10.0)
rect_x2 = input(defval=0)
rect_y2 = input(defval=20.0)
rect_xloc = input(defval=xloc.bar_index, options=[xloc.bar_index, xloc.bar_time])
rect_xtend = input(defval=extend.none, options=[extend.none, extend.right, extend.left, extend.both])
rect_style = input(defval=line.style_dotted, options=[line.style_solid, line.style_dotted, line.style_dashed, line.style_arrow_left, line.style_arrow_right, line.style_arrow_both])
rect_width = input(2, minval=0)
if show_rectangle and barstate.islast and barstate.ishistory[1]
    _adjust_x1 = rect_xloc == xloc.bar_index ? bar_index - rect_x1 : timenow + rect_x1 * 60000
    _adjust_x2 = rect_xloc == xloc.bar_index ? bar_index - rect_x2 : timenow + rect_x2 * 60000
    f_line_rectangle(
         _adjust_x1, rect_y1, 
         _adjust_x2, rect_y2, 
         rect_xloc, rect_xtend, 
         color.new(#00ffff, 50),  rect_style, rect_width 
         )
//  ||  |}─────────────────────────────────────────────────────────────────────||
```
</details>

##### Code Author(s):
  * ##### [Ricardo Santos](https://www.tradingview.com/u/RicardoSantos/ "@Tradingview.") 

<br/>
<br/>
<br/>

[Disclaimer](/./DISCLAIMER.md "Disclaimer.")<br/>
[License](/./LICENSE "License.")
