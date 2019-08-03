![PineCoders](/images/PineCodersLong.png "PineCoders")

# Function to generate random values within range

#### Description:

Function to generate random values.
The returned value will be a float value within range `0 -> _range` parameter.

##### References:
* [link1](https://www.tradingcode.net/tradingview/colours/random-colours/ "link1")
* [link2](https://cdsmith.wordpress.com/2011/10/10/build-your-own-simple-random-numbers/ "link2")


#### Code:

<details open>
  <!-- leave a blank line after summary -->
  <summary>@version=3</summary>

```javascript
f_pseudo_random_number(_range, _seed)=>
//  ||-------------------------------------------------------------------------||
//  ||  Basic Pseudo Random Value generator                                    ||
//  ||-------------------------------------------------------------------------||
//  |{
//  ||  Author: Ricardo Santos
//  ||  reference:
//  ||      https://www.tradingcode.net/tradingview/colours/random-colours/
//  ||      https://cdsmith.wordpress.com/2011/10/10/build-your-own-simple-random-numbers/
//  ||      x = 16708 * nz(x[1], 1) % 2147483647
//  ||-------------------------------------------------------------------------||
    _return = 1.0
    if na(_seed)
        _return := 3.14159 * nz(_return[1], 1) % n
    else
        _return := 3.14159 * nz(_return[1], 1) % (n + _seed)
    _return := _return % (_range)
//  }|--------------------------------------------------------------------<•
```
</details>


#### Example:


Generate a random value between 0 and 100 <br/>

<details open>
  <!-- leave a blank line after summary -->
  <summary>Example Code</summary>

<!--  -->
<!-- code goes between the backticks: -->
```javascript
//@version=3
study("Function - Pseudo Random Number Example")

f_pseudo_random_number(_range, _seed)=>
//  ||-------------------------------------------------------------------------||
//  ||  Basic Pseudo Random Value generator                                    ||
//  ||-------------------------------------------------------------------------||
//  |{
//  ||  Author: Ricardo Santos
//  ||  reference:
//  ||      https://www.tradingcode.net/tradingview/colours/random-colours/
//  ||      https://cdsmith.wordpress.com/2011/10/10/build-your-own-simple-random-numbers/
//  ||      x = 16708 * nz(x[1], 1) % 2147483647
//  ||-------------------------------------------------------------------------||
    _return = 1.0
    if na(_seed)
        _return := 3.14159 * nz(_return[1], 1) % n
    else
        _return := 3.14159 * nz(_return[1], 1) % (n + _seed)
    _return := _return % (_range)
//  }|--------------------------------------------------------------------<•

range = 100.0
math_e = 2.7182818285 // Euler's number
example = f_pseudo_random_number(range, math_e)
plot(series=example, title='example', color=red)

```
</details>

##### Code Author(s):
  * ##### [Ricardo Santos](https://www.tradingview.com/u/RicardoSantos/ "@Tradingview.") 

<br/>
<br/>
<br/>

[Disclaimer](/./DISCLAIMER.md "Disclaimer.")<br/>
[License](/./LICENSE "License.")
