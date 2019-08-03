![PineCoders](/images/PineCodersLong.png "PineCoders")

# Function to return the days in a specified month.

#### Description:

Function to determine how many days a month has.

##### References:
* [link1](https://cmcenroe.me/2014/12/05/days-in-month-formula.html "link1")


#### Code:

<details open>
  <!-- leave a blank line after summary -->
  <summary>@version=4</summary>

```javascript
f_daysinmonth(_year, _month)=>
//	|{
//	||	Author: Ricardo Santos, Ari Faynerman
//	||	Description: returns how many days there is in specified month.
//	||	Reference:
//	||		https://cmcenroe.me/2014/12/05/days-in-month-formula.html
//	||
    _m = _month < 1 ? 1 : _month > 12 ? 12 : _month
    28 + (_m == 2 and _year % 4 == 0 ? 1 : 0) + (_m + floor(_m / 8)) % 2 + 2 % _m + 2 * floor(1 / _m)
//	}|
```
</details>


#### Example:

Return how many days are in a specified month. <br/>

<details open>
  <!-- leave a blank line after summary -->
  <summary>Example Code</summary>

<!--  -->
<!-- code goes between the backticks: -->
```javascript
//@version=4
study(title="[RS]Function - Days in a Month")

f_daysinmonth(_year, _month)=>
//	|{
//	||	Author: Ricardo Santos, Ari Faynerman
//	||	Description: returns how many days there is in specified month.
//	||	Reference:
//	||		https://cmcenroe.me/2014/12/05/days-in-month-formula.html
//	||
    _m = _month < 1 ? 1 : _month > 12 ? 12 : _month
    28 + (_m == 2 and _year % 4 == 0 ? 1 : 0) + (_m + floor(_m / 8)) % 2 + 2 % _m + 2 * floor(1 / _m)
//	}|

m = f_daysinmonth(input(2019), input(1))
plot(m)

```
</details>

##### Code Author(s):
  * ##### [Ricardo Santos](https://www.tradingview.com/u/RicardoSantos/ "@Tradingview.") 
  * ##### [Ari Faynerman](https://www.tradingview.com/u/a.tesla2018/ "@Tradingview.") 

<br/>
<br/>
<br/>

[Disclaimer](/./DISCLAIMER.md "Disclaimer.")<br/>
[License](/./LICENSE "License.")
