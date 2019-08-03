![PineCoders](/images/PineCodersLong.png "PineCoders")

# Function to draw a Trapezoid on chart.

#### Description:

Function that draws a trapezoid.

##### References:
* [noreference](/ "No Reference.")


#### Code:

<details open>
  <!-- leave a blank line after summary -->
  <summary>@version=4</summary>

```javascript
//  ||─────────────────────────────────────────────────────────────────────────||
//  ||  Draw a Trapezoid with 4 vector2D(x, y) coordinates:
//  ||─────────────────────────────────────────────────────────────────────────||
//  |{─────────────────────────────────────────────────────────────────────────||
//  ||  Parameters:
//  ||      _x1, _y1    (series )   : 1st vector2D(x, y) coordinates.
//  ||      _x2, _y2    (series )   : 2nd vector2D(x, y) coordinates.
//  ||      _x3, _y3    (series )   : 3rd vector2D(x, y) coordinates.
//  ||      _x4, _y4    (series )   : 4th vector2D(x, y) coordinates.
//  ||      _xloc       (string )   : options: xloc.bar_index and xloc.bar_time. 
//  ||      _extend     (string )   : options: extend.none, extend.right, extend.left, extend.both
//  ||      _color      (color  )   : color code ex:. #000000, color.black, color.new(#000000, 40)
//  ||      _style      (string )   : options: : line.style_solid, line.style_dotted, line.style_dashed, line.style_arrow_left, line.style_arrow_right, line.style_arrow_both
//  ||      _width      (integer)   : width in pixels.
f_line_trapezoid(_x1, _y1, _x2, _y2, _x3, _y3, _x4, _y4, _xloc, _extend, _color, _style, _width)=>
    //    (x2,y2) Side2 (x3, y3)
    //          ┌───────┐
    //          │       │
    //   Side1  │       │ Side3
    //          │       │
    //          └───────┘
    //    (x1,y1) Side4 (x4, y4)
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
         x2 = _x2, y2 = _y2, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side2 := line.new(
         x1 = _x2, y1 = _y2, 
         x2 = _x3, y2 = _y3, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side3 := line.new(
         x1 = _x3, y1 = _y3, 
         x2 = _x4, y2 = _y4, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side4 := line.new(
         x1 = _x4, y1 = _y4, 
         x2 = _x1, y2 = _y1, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
//  ||─────────────────────────────────────────────────────────────────────────||

```
</details>


#### Example:

Draws a  trapezoid on chart.<br/>

<details open>
  <!-- leave a blank line after summary -->
  <summary>Example Code</summary>

<!--  -->
<!-- code goes between the backticks: -->
```javascript
//@version=4
study(title="[RS]Function - Geometric Line Drawings")

//  ||─────────────────────────────────────────────────────────────────────────||
//  ||  Draw a Trapezoid with 4 vector2D(x, y) coordinates:
//  ||─────────────────────────────────────────────────────────────────────────||
//  |{─────────────────────────────────────────────────────────────────────────||
//  ||  Parameters:
//  ||      _x1, _y1    (series )   : 1st vector2D(x, y) coordinates.
//  ||      _x2, _y2    (series )   : 2nd vector2D(x, y) coordinates.
//  ||      _x3, _y3    (series )   : 3rd vector2D(x, y) coordinates.
//  ||      _x4, _y4    (series )   : 4th vector2D(x, y) coordinates.
//  ||      _xloc       (string )   : options: xloc.bar_index and xloc.bar_time. 
//  ||      _extend     (string )   : options: extend.none, extend.right, extend.left, extend.both
//  ||      _color      (color  )   : color code ex:. #000000, color.black, color.new(#000000, 40)
//  ||      _style      (string )   : options: : line.style_solid, line.style_dotted, line.style_dashed, line.style_arrow_left, line.style_arrow_right, line.style_arrow_both
//  ||      _width      (integer)   : width in pixels.
f_line_trapezoid(_x1, _y1, _x2, _y2, _x3, _y3, _x4, _y4, _xloc, _extend, _color, _style, _width)=>
    //    (x2,y2) Side2 (x3, y3)
    //          ┌───────┐
    //          │       │
    //   Side1  │       │ Side3
    //          │       │
    //          └───────┘
    //    (x1,y1) Side4 (x4, y4)
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
         x2 = _x2, y2 = _y2, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side2 := line.new(
         x1 = _x2, y1 = _y2, 
         x2 = _x3, y2 = _y3, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side3 := line.new(
         x1 = _x3, y1 = _y3, 
         x2 = _x4, y2 = _y4, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
    _side4 := line.new(
         x1 = _x4, y1 = _y4, 
         x2 = _x1, y2 = _y1, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
//  ||─────────────────────────────────────────────────────────────────────────||
//  ||  Example:
show_trapezoid = input(true)
trapezoid_x1 = input(defval=15)
trapezoid_y1 = input(defval=4.0)
trapezoid_x2 = input(defval=10)
trapezoid_y2 = input(defval=25.0)
trapezoid_x3 = input(defval=5)
trapezoid_y3 = input(defval=20.0)
trapezoid_x4 = input(defval=2)
trapezoid_y4 = input(defval=2.0)
trapezoid_xloc = input(defval=xloc.bar_index, options=[xloc.bar_index, xloc.bar_time])
trapezoid_xtend = input(defval=extend.none, options=[extend.none, extend.right, extend.left, extend.both])
trapezoid_style = input(defval=line.style_dashed, options=[line.style_solid, line.style_dotted, line.style_dashed, line.style_arrow_left, line.style_arrow_right, line.style_arrow_both])
trapezoid_width = input(2, minval=0)
if show_trapezoid and barstate.islast and barstate.ishistory[1]
    _adjust_x1 = rect_xloc == xloc.bar_index ? bar_index - trapezoid_x1 : timenow + trapezoid_x1 * 60000
    _adjust_x2 = rect_xloc == xloc.bar_index ? bar_index - trapezoid_x2 : timenow + trapezoid_x2 * 60000
    _adjust_x3 = rect_xloc == xloc.bar_index ? bar_index - trapezoid_x3 : timenow + trapezoid_x3 * 60000
    _adjust_x4 = rect_xloc == xloc.bar_index ? bar_index - trapezoid_x4 : timenow + trapezoid_x4 * 60000
    f_line_trapezoid(
         _adjust_x1, trapezoid_y1, 
         _adjust_x2, trapezoid_y2, 
         _adjust_x3, trapezoid_y3, 
         _adjust_x4, trapezoid_y4, 
         trapezoid_xloc, trapezoid_xtend, 
         color.new(#ff5500, 50),  trapezoid_style, trapezoid_width 
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
