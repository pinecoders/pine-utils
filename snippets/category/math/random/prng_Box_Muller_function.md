![PineCoders](/images/PineCodersLong.png "PineCoders")

# Function to generate random values using Box Muller technique

#### Description:

Function to generate random values.
The returned value will be a uncapped float value, with bias towards a normal distribution.


##### References:
* [link1](https://www.howtoexcel.org/statistics/normal-distribution/ "link1")
* [link2](https://www.excelfunctions.net/excel-ln-function.html "link2")
* [link3](https://www.google.pt/search?q=function+to+apply+a+random+value+from+bell+curve "link3")


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
f_pseudo_random_bm(_mean, _dev, _seed)=>
//  ||-------------------------------------------------------------------------||
//  ||  Adaptation for Box Muller Method To Generate Random Normal Values      ||
//  ||-------------------------------------------------------------------------||
//  |{
//  ||  Author: Ricardo Santos
//  ||		reference:
//  ||			https://www.howtoexcel.org/statistics/normal-distribution/
//  ||			https://www.excelfunctions.net/excel-ln-function.html
//  ||			https://www.google.pt/search?q=function+to+apply+a+random+value+from+bell+curve
//  ||			
//  ||			sqrt(-2*log(RAND()))*cos(2*PI()*RAND())*StdDev+Mean
//  ||			    Mean – This is the mean of the normal distribution.
//  ||			    StdDev – This is the standard deviation of the normal distributed.
//  ||			Notes:
//  ||			    Uncapped values.
//  ||-------------------------------------------------------------------------||
    _pi = 3.14159265359
    _random_1 = f_pseudo_random_number(1.0, _seed)
    _random_2 = f_pseudo_random_number(1.0, -_seed)
    _return = sqrt(-2 * log(_random_1)) * cos(2 * _pi * _random_2) * _dev + _mean
//  }|--------------------------------------------------------------------<•
```
</details>


#### Example:

Generate a random value with bias towards a normal distribution, the value generated will be unbound. <br/>

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
f_pseudo_random_bm(_mean, _dev, _seed)=>
//  ||-------------------------------------------------------------------------||
//  ||  Adaptation for Box Muller Method To Generate Random Normal Values      ||
//  ||-------------------------------------------------------------------------||
//  |{
//  ||  Author: Ricardo Santos
//  ||		reference:
//  ||			https://www.howtoexcel.org/statistics/normal-distribution/
//  ||			https://www.excelfunctions.net/excel-ln-function.html
//  ||			https://www.google.pt/search?q=function+to+apply+a+random+value+from+bell+curve
//  ||			
//  ||			sqrt(-2*log(RAND()))*cos(2*PI()*RAND())*StdDev+Mean
//  ||			    Mean – This is the mean of the normal distribution.
//  ||			    StdDev – This is the standard deviation of the normal distributed.
//  ||			Notes:
//  ||			    Uncapped values.
//  ||-------------------------------------------------------------------------||
    _pi = 3.14159265359
    _random_1 = f_pseudo_random_number(1.0, _seed)
    _random_2 = f_pseudo_random_number(1.0, -_seed)
    _return = sqrt(-2 * log(_random_1)) * cos(2 * _pi * _random_2) * _dev + _mean
//  }|--------------------------------------------------------------------<•


mean = input(0.1)
dev = input(0.5)
rng = f_nd_pseudo_random(mean, dev, input(1.0))

plot(series=rng, title="Normally Distributed Pseudo Random Value", color=red, linewidth=2, style=circles, transp=0)
hline(mean)
hline(mean+dev)
hline(mean-dev)

```
</details>

##### Code Author(s):
  * ##### [Ricardo Santos](https://www.tradingview.com/u/RicardoSantos/ "@Tradingview.") 

<br/>
<br/>
<br/>

[Disclaimer](/./DISCLAIMER.md "Disclaimer.")<br/>
[License](/./LICENSE "License.")
