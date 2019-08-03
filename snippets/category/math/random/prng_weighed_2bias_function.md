![PineCoders](/images/PineCodersLong.png "PineCoders")

# Function to generate random values with bias towards a range within a range

#### Description:

Function to generate random values.
The returned value will be a float value with bias towards a range within a range.

##### References:
* [nolink](/ "nolink")



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
//  ||-------------------------------------------------------------------------||
    _return = 1.0
    if na(_seed)
        _return := 3.14159 * nz(_return[1], 1) % n
    else
        _return := 3.14159 * nz(_return[1], 1) % (n + _seed)
    _return := _return % (_range)
//  }|--------------------------------------------------------------------<•
f_weighted_dist_double_bias_prng(_min, _max, _center, _side, _distribution, _seed)=>
//  ||-------------------------------------------------------------------------||
//  ||  Weighted Distribution with centered bias                                 ||
//  ||-------------------------------------------------------------------------||
//  |{
//  ||  Author: Ricardo Santos
//  ||		Notes:
//  ||   		The purpose is to generate a value where the generation trends towards
//  ||		    the level value and side of the bias level(over/under bias level)
//  ||-------------------------------------------------------------------------||
    _upper_range = _max - _center
    _lower_range = _center - _min
    _rng = f_pseudo_random_number(1.0, _seed)
    _return = na
    if _rng > _side
        _return := _center + (0.0 + _upper_range * pow(_rng * (1/_side) - 1, _distribution))
    else
        _return := _center - (0.0 + _lower_range * pow(1 - _rng * (1/_side), _distribution))
    _return
//  }|--------------------------------------------------------------------<•
```
</details>


#### Example:


Generate a random value with bias towards a range within a range. <br/>

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
//  ||-------------------------------------------------------------------------||
    _return = 1.0
    if na(_seed)
        _return := 3.14159 * nz(_return[1], 1) % n
    else
        _return := 3.14159 * nz(_return[1], 1) % (n + _seed)
    _return := _return % (_range)
//  }|--------------------------------------------------------------------<•
f_weighted_dist_double_bias_prng(_min, _max, _center, _side, _distribution, _seed)=>
//  ||-------------------------------------------------------------------------||
//  ||  Weighted Distribution with centered bias                                 ||
//  ||-------------------------------------------------------------------------||
//  |{
//  ||  Author: Ricardo Santos
//  ||		Notes:
//  ||   		The purpose is to generate a value where the generation trends towards
//  ||		    the level value and side of the bias level(over/under bias level)
//  ||-------------------------------------------------------------------------||
    _upper_range = _max - _center
    _lower_range = _center - _min
    _rng = f_pseudo_random_number(1.0, _seed)
    _return = na
    if _rng > _side
        _return := _center + (0.0 + _upper_range * pow(_rng * (1/_side) - 1, _distribution))
    else
        _return := _center - (0.0 + _lower_range * pow(1 - _rng * (1/_side), _distribution))
    _return
//  }|--------------------------------------------------------------------<•

double_bias_center = input(0.618)
double_bias_side = input(0.5)
double_bias_distribution = input(3.14159265359)
double_bias_prng = f_weighted_dist_double_bias_prng( 
         0.0, 
         1.0, 
         double_bias_center,
         double_bias_side, 
         double_bias_distribution, 
         1.0
         )
plot(series=double_bias_prng, title="Weighted Distribution with direction centered bias", color=purple, linewidth=2, style=circles, transp=0)
```
</details>

##### Code Author(s):
  * ##### [Ricardo Santos](https://www.tradingview.com/u/RicardoSantos/ "@Tradingview.") 

<br/>
<br/>
<br/>

[Disclaimer](/./DISCLAIMER.md "Disclaimer.")<br/>
[License](/./LICENSE "License.")
