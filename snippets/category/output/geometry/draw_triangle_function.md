![PineCoders](/images/PineCodersLong.png "PineCoders")

# Function to draw a triangle on chart.

#### Description:

Function that draws a triangle.

##### References:
* [noreference](/ "No Reference.")


#### Code:

<details open>
  <!-- leave a blank line after summary -->
  <summary>@version=4</summary>

```javascript
//  ||─────────────────────────────────────────────────────────────────────────||
//  ||  Draw a Triangle with 3 vector2D(x, y) coordinates:
//  ||─────────────────────────────────────────────────────────────────────────||
//  |{─────────────────────────────────────────────────────────────────────────||
//  ||  Parameters:
//  ||      _x1, _y1    (series )   : first vector2D(x, y) coordinates.
//  ||      _x2, _y2    (series )   : second vector2D(x, y) coordinates.
//  ||      _x3, _y3    (series )   : second vector2D(x, y) coordinates.
//  ||      _xloc       (string )   : options: xloc.bar_index and xloc.bar_time. 
//  ||      _extend     (string )   : options: extend.none, extend.right, extend.left, extend.both
//  ||      _color      (color  )   : color code ex:. #000000, color.black, color.new(#000000, 40)
//  ||      _style      (string )   : options: : line.style_solid, line.style_dotted, line.style_dashed, line.style_arrow_left, line.style_arrow_right, line.style_arrow_both
//  ||      _width      (integer)   : width in pixels.
f_line_triangle(_x1, _y1, _x2, _y2, _x3, _y3, _xloc, _extend, _color, _style, _width)=>
    //              (x2, y2)
    //                  ┐
    //                ∕ │
    //        Side1 ∕   │ Side2
    //            ⁄     │
    //          └───────┘
    //    (x1,y1) Side3 (x3, y3)
    var line _side1 = na
    var line _side2 = na
    var line _side3 = na
    
    //  clear previous lines: 
    line.delete(_side1)
    line.delete(_side2)
    line.delete(_side3)

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
         x2 = _x1, y2 = _y1, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
//  ||─────────────────────────────────────────────────────────────────────────||

```
</details>


#### Example:

Draws a  triangle on chart.<br/>

<details open>
  <!-- leave a blank line after summary -->
  <summary>Example Code</summary>

<!--  -->
<!-- code goes between the backticks: -->
```javascript
//@version=4
study(title="[RS]Function - Geometric Line Drawings")

//  ||─────────────────────────────────────────────────────────────────────────||
//  ||  Draw a Triangle with 3 vector2D(x, y) coordinates:
//  ||─────────────────────────────────────────────────────────────────────────||
//  |{─────────────────────────────────────────────────────────────────────────||
//  ||  Parameters:
//  ||      _x1, _y1    (series )   : first vector2D(x, y) coordinates.
//  ||      _x2, _y2    (series )   : second vector2D(x, y) coordinates.
//  ||      _x3, _y3    (series )   : second vector2D(x, y) coordinates.
//  ||      _xloc       (string )   : options: xloc.bar_index and xloc.bar_time. 
//  ||      _extend     (string )   : options: extend.none, extend.right, extend.left, extend.both
//  ||      _color      (color  )   : color code ex:. #000000, color.black, color.new(#000000, 40)
//  ||      _style      (string )   : options: : line.style_solid, line.style_dotted, line.style_dashed, line.style_arrow_left, line.style_arrow_right, line.style_arrow_both
//  ||      _width      (integer)   : width in pixels.
f_line_triangle(_x1, _y1, _x2, _y2, _x3, _y3, _xloc, _extend, _color, _style, _width)=>
    //              (x2, y2)
    //                  ┐
    //                ∕ │
    //        Side1 ∕   │ Side2
    //            ⁄     │
    //          └───────┘
    //    (x1,y1) Side3 (x3, y3)
    var line _side1 = na
    var line _side2 = na
    var line _side3 = na
    
    //  clear previous lines: 
    line.delete(_side1)
    line.delete(_side2)
    line.delete(_side3)

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
         x2 = _x1, y2 = _y1, 
         xloc = _xloc, extend = _extend, 
         color = _color, style = _style, width = _width 
         )
//  ||─────────────────────────────────────────────────────────────────────────||
//  ||  Example:
show_triangle = input(true)
triangle_x1 = input(defval=4)
triangle_y1 = input(defval=4.0)
triangle_x2 = input(defval=0)
triangle_y2 = input(defval=18.0)
triangle_x3 = input(defval=8)
triangle_y3 = input(defval=15.0)
triangle_xloc = input(defval=xloc.bar_index, options=[xloc.bar_index, xloc.bar_time])
triangle_xtend = input(defval=extend.none, options=[extend.none, extend.right, extend.left, extend.both])
triangle_style = input(defval=line.style_solid, options=[line.style_solid, line.style_dotted, line.style_dashed, line.style_arrow_left, line.style_arrow_right, line.style_arrow_both])
triangle_width = input(2, minval=0)
if show_triangle and barstate.islast and barstate.ishistory[1]
    _adjust_x1 = rect_xloc == xloc.bar_index ? bar_index - triangle_x1 : timenow + triangle_x1 * 60000
    _adjust_x2 = rect_xloc == xloc.bar_index ? bar_index - triangle_x2 : timenow + triangle_x2 * 60000
    _adjust_x3 = rect_xloc == xloc.bar_index ? bar_index - triangle_x3 : timenow + triangle_x3 * 60000
    f_line_triangle(
         _adjust_x1, triangle_y1, 
         _adjust_x2, triangle_y2, 
         _adjust_x3, triangle_y3, 
         triangle_xloc, triangle_xtend, 
         color.new(#5555ff, 50),  triangle_style, triangle_width 
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
