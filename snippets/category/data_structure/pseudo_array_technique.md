![PineCoders](/images/PineCodersLong.png "PineCoders")

# Pseudo Array prototype - Technique

#### Description:

Demonstration on how to create a pseudo array in Pine script.

##### References:
  * [noreference](/ "link1")

#### Code:

<details close>
  <!-- leave a blank line after summary -->
  <summary>@version=4:</summary>

```javascript

```
</details>


#### Example:

Demonstration on how to create a pseudo array in Pine script.<br/>

<details open>
  <!-- leave a blank line after summary -->
  <!--<summary>Code:</summary> -->

<!--  -->
<!-- code goes between the backticks: -->
```javascript
//@version=4
study(title="[RS]Multi length pseudo Array Example")

//  ||-------------------------------------------------------------------------||
//  ||  Pseudo Array Generic code: (ID)
//  |{-------------------------------------------------------------------------<•
//  ||  variable initialization:
var float A00 = na
var float A01 = na, var float A11 = na, var float A21 = na, var float A31 = na
var float A02 = na, var float A12 = na, var float A22 = na, var float A32 = na
var float A03 = na, var float A13 = na, var float A23 = na, var float A33 = na
var float A04 = na, var float A14 = na, var float A24 = na, var float A34 = na
var float A05 = na, var float A15 = na, var float A25 = na, var float A35 = na
var float A06 = na, var float A16 = na, var float A26 = na, var float A36 = na
var float A07 = na, var float A17 = na, var float A27 = na, var float A37 = na
var float A08 = na, var float A18 = na, var float A28 = na, var float A38 = na
var float A09 = na, var float A19 = na, var float A29 = na, var float A39 = na
var float A10 = na, var float A20 = na, var float A30 = na, var float A40 = na

var int ALEN = 5
float ASET = na
//  |{-------------------------------------------------------------------------<•
//  ||  Utility Functions: (ID)
f_AGET(_i)=>_i==0?A00:_i==1?A01:_i==2?A02:_i==3?A03:_i==4?A04:_i==5?A05:_i==6?A06:_i==7?A07:_i==8?A08:_i==9?A09:_i==10?A10:_i==11?A11:_i==12?A12:_i==13?A13:_i==14?A14:_i==15?A15:_i==16?A16:_i==17?A17:_i==18?A18:_i==19?A19:_i==20?A20:_i==21?A21:_i==22?A22:_i==23?A23:_i==24?A24:_i==25?A25:_i==26?A26:_i==27?A27:_i==28?A28:_i==29?A29:_i==30?A30:_i==31?A31:_i==32?A32:_i==33?A33:_i==34?A34:_i==35?A35:_i==36?A36:_i==37?A37:_i==38?A38:_i==39?A39:_i==40?A40:na
f_ASET(_value, _index, _length)=>
    float _return = na
    if _index > _length
        _return := na
    else
        if _index == 0
            _return := _value
        else
            _return := f_AGET(_index-1)
    _return
//  ||  |}---------------------------------------------------------------------<•

//  ||  |}---------------------------------------------------------------------<•

AEVENT = bar_index == 3
AEVENT2 = bar_index == 50
AEVENT3 = bar_index == 100

if AEVENT
    ASET := 3
if AEVENT2
    ASET := 50
if AEVENT3
    ASET := 100

//  |{-------------------------------------------------------------------------<•
//  ||  update array: (ID)
//  ||      • this must/should be right after event.
//  ||      • if theres more than one event per bar the code bellow must be 
//  ||          repeated to update the array. its possible to change f_ASET()
//  ||          so that you can update multiple positions if they dont interact
if not na(ASET)
	A40 := f_ASET(ASET, 40, ALEN), A39 := f_ASET(ASET, 39, ALEN), A38 := f_ASET(ASET, 38, ALEN), A37 := f_ASET(ASET, 37, ALEN), A36 := f_ASET(ASET, 36, ALEN)
	A35 := f_ASET(ASET, 35, ALEN), A34 := f_ASET(ASET, 34, ALEN), A33 := f_ASET(ASET, 33, ALEN), A32 := f_ASET(ASET, 32, ALEN), A31 := f_ASET(ASET, 31, ALEN)
	A30 := f_ASET(ASET, 30, ALEN), A29 := f_ASET(ASET, 29, ALEN), A28 := f_ASET(ASET, 28, ALEN), A27 := f_ASET(ASET, 27, ALEN), A26 := f_ASET(ASET, 26, ALEN)
	A25 := f_ASET(ASET, 25, ALEN), A24 := f_ASET(ASET, 24, ALEN), A23 := f_ASET(ASET, 23, ALEN), A22 := f_ASET(ASET, 22, ALEN), A21 := f_ASET(ASET, 21, ALEN)
	A20 := f_ASET(ASET, 20, ALEN), A19 := f_ASET(ASET, 19, ALEN), A18 := f_ASET(ASET, 18, ALEN), A17 := f_ASET(ASET, 17, ALEN), A16 := f_ASET(ASET, 16, ALEN)
	A15 := f_ASET(ASET, 15, ALEN), A14 := f_ASET(ASET, 14, ALEN), A13 := f_ASET(ASET, 13, ALEN), A12 := f_ASET(ASET, 12, ALEN), A11 := f_ASET(ASET, 11, ALEN)
	A10 := f_ASET(ASET, 10, ALEN), A09 := f_ASET(ASET, 09, ALEN), A08 := f_ASET(ASET, 08, ALEN), A07 := f_ASET(ASET, 07, ALEN), A06 := f_ASET(ASET, 06, ALEN)
	A05 := f_ASET(ASET, 05, ALEN), A04 := f_ASET(ASET, 04, ALEN), A03 := f_ASET(ASET, 03, ALEN), A02 := f_ASET(ASET, 02, ALEN), A01 := f_ASET(ASET, 01, ALEN)
	A00 := f_ASET(ASET, 00, ALEN)
//  ||  |}---------------------------------------------------------------------<•

f_draw_infopanel(_x, _y, _line, _text)=>
    _rep_text = ""
    for _l = 0 to _line
        _rep_text := _rep_text + "\n"
    _rep_text := _rep_text + _text
    var label _la = na
    label.delete(_la)
    _la := label.new(
         x=_x, y=_y, 
         text=_rep_text, xloc=xloc.bar_time, yloc=yloc.price, 
         color=color.black, style=label.style_labelup, textcolor=color.silver, size=size.large)
         //)

lapos_x = timenow + round(change(time)*100)
lapos_y = 0.0//highest(20)
f_draw_infopanel(lapos_x, lapos_y, 00, "00 - " + tostring(A00[0]) + "\n" + "01 - " + tostring(A01[0]) + "\n" + "02 - " + tostring(A02[0]) + "\n" + "03 - " + tostring(A03[0]) + "\n" + "04 - " + tostring(A04[0]) + "\n" + "05 - " + tostring(A05[0]) + "\n" + "06 - " + tostring(A06[0]) + "\n" + "07 - " + tostring(A07[0]) + "\n" + "08 - " + tostring(A08[0]) + "\n" + "09 - " + tostring(A09[0]) + "\n" + "10 - " + tostring(A10[0]))
```
</details>

##### Code Author(s):
  * ##### [Ricardo Santos](https://www.tradingview.com/u/RicardoSantos/ "@Tradingview.") 

<br/>
<br/>
<br/>

[Disclaimer](/./DISCLAIMER.md "Disclaimer.")<br/>
[License](/./LICENSE "License.")
