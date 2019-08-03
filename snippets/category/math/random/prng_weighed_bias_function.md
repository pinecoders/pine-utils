![PineCoders](/images/PineCodersLong.png "PineCoders")

# Function to generate random values with weighted bias

#### Description:

Function to generate random values.
The returns a float value, with bias towards a level.

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
//  ||-------------------------------------------------------------------------||
//  ||  Weighted Distribution with a bias                                      ||
//  ||-------------------------------------------------------------------------||
//  |{
//  ||  Author: Ricardo Santos
//  ||-------------------------------------------------------------------------||
f_weighted_dist_bias_prng(_min, _max, _center, _distribution, _seed)=>
    _upper_range = _max - _center
    _lower_range = _center - _min
    _rng = f_pseudo_random_number(1.0, _seed)
    _return = na
    if _rng > 0.5
        _return := _center + (0.0 + _upper_range * pow(_rng * 2 - 1, _distribution))
    else
        _return := _center - (0.0 + _upper_range * pow(1 - _rng * 2, _distribution))
    _return
//  }|--------------------------------------------------------------------<•
```
</details>


#### Example:

Generate a random value with bias towards a level. <br/>

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
//  ||-------------------------------------------------------------------------||
//  ||  Weighted Distribution with a bias                                      ||
//  ||-------------------------------------------------------------------------||
//  |{
//  ||  Author: Ricardo Santos
//  ||-------------------------------------------------------------------------||
f_weighted_dist_bias_prng(_min, _max, _center, _distribution, _seed)=>
    _upper_range = _max - _center
    _lower_range = _center - _min
    _rng = f_pseudo_random_number(1.0, _seed)
    _return = na
    if _rng > 0.5
        _return := _center + (0.0 + _upper_range * pow(_rng * 2 - 1, _distribution))
    else
        _return := _center - (0.0 + _upper_range * pow(1 - _rng * 2, _distribution))
    _return
//  }|--------------------------------------------------------------------<•

bias_distribution = input(3.14159265359)
bias_center = input(0.618)
wdb_prng = f_weighted_dist_bias_prng(0.0, 1.0, bias_center, bias_distribution, 1.0)
plot(series=wdb_prng, title="Weighted Distribution with a bias", color=orange, linewidth=2, style=circles, transp=0)
```
</details>

##### Code Author(s):
  * ##### [Ricardo Santos](https://www.tradingview.com/u/RicardoSantos/ "@Tradingview.") 

<br/>
<br/>
<br/>

[Disclaimer](/./DISCLAIMER.md "Disclaimer.")<br/>
[License](/./LICENSE "License.")
