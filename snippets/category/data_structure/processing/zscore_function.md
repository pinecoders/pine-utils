![PineCoders](/images/PineCodersLong.png "PineCoders")

# Standardization Z Score Function

#### Description:

A Function to apply zscore standardization to any data series.
Zscore returns a series were the mean is 0 and one standard deviation is 1.

##### References:
  * [Link1](https://www.statisticshowto.datasciencecentral.com/standardized-values-examples/ "link1")

#### Code:

<details open>
  <!-- leave a blank line after summary -->
  <summary>@version=4:</summary>

```javascript
f_zscore(_src, _length, _smooth)=>
//  ||-------------------------------------------------------------------------||
//  ||  Standardization/zscore Function                                    ||
//  ||-------------------------------------------------------------------------||
//  |{
//  ||  Author: Ricardo Santos
//  ||  References: 
//  ||      https://www.statisticshowto.datasciencecentral.com/standardized-values-examples/
//  ||-------------------------------------------------------------------------||
    _mean = sma(_src, _length)
    _std = stdev(_src-_mean, _length)
    _value = (_src - _mean) / _std
    _return = ema(ema(_value, _smooth), _smooth)
//  }|--------------------------------------------------------------------<•
```
</details>


#### Example:

zScore considering multiple applied lengths.<br/>

<details open>
  <!-- leave a blank line after summary -->
  <!--<summary>Code:</summary> -->

<!--  -->
<!-- code goes between the backticks: -->
```javascript
//@version=4
study(title="[RS]Function - Standardization - zScore")

f_zscore(_src, _length, _smooth)=>
//  ||-------------------------------------------------------------------------||
//  ||  Standardization/zscore Function                                    ||
//  ||-------------------------------------------------------------------------||
//  |{
//  ||  Author: Ricardo Santos
//  ||  References: 
//  ||      https://www.statisticshowto.datasciencecentral.com/standardized-values-examples/
//  ||-------------------------------------------------------------------------||
    _mean = sma(_src, _length)
    _std = stdev(_src-_mean, _length)
    _value = (_src - _mean) / _std
    _return = ema(ema(_value, _smooth), _smooth)
//  }|--------------------------------------------------------------------<•

smooth = input(8)
f0 = f_zscore(close, input(6), smooth)
f1 = f_zscore(close, input(14), smooth)
f2 = f_zscore(close, input(26), smooth)
f3 = f_zscore(close, input(100), smooth)

plot(series=f0, color=color.green, style=plot.style_area)
plot(series=f1, color=color.lime, style=plot.style_area)
plot(series=f2, color=color.red, style=plot.style_area)
plot(series=f3, color=color.maroon, style=plot.style_area)

hline(0)
```
</details>

##### Code Author(s):
  * ##### [Ricardo Santos](https://www.tradingview.com/u/RicardoSantos/ "@Tradingview.") 

<br/>
<br/>
<br/>

[Disclaimer](/./DISCLAIMER.md "Disclaimer.")<br/>
[License](/./LICENSE "License.")
