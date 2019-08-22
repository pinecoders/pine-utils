![PineCoders](/images/PineCodersLong.png "PineCoders")

# Your Snippet Name

#### Description:

Place description of your snippet here.

<!-- optional -->
##### References:
  * [Link](http:\\alinktonowhere.come "description_of_link")

#### Code:

<details open>
  <!-- leave a blank line after summary -->
  <summary>@version=4:</summary>

```
f_phi() =>
    float _phi = 0.5 + sqrt(1.25)
    _phi
```
</details>

<details close>
  <!-- leave a blank line after summary -->
  <summary>@version=2:</summary>

<!-- code goes between the backticks: -->
```javascript
f_phi() =>
    _phi = 0.5 + sqrt(1.25)
    _phi
```
</details>

<!-- optional -->
#### Example:

Place description of the example here.<br/>

<details open>
  <!-- leave a blank line after summary -->
  <summary>&nbsp;</summary>

<!-- code goes between the backticks: -->
```javascript
//@version=4
study("Function - Golden Ratio")

f_phi() =>
    float _phi = 0.5 + sqrt(1.25)
    _phi

example = f_phi() * 2
plot(series=example, title="Example", color=color.red)

```
</details>

<!-- optional -->
##### Code Author(s):
  * [Author](http:\\linkifavaiable "@nickname")

<br/>
<br/>

[Disclaimer](/./DISCLAIMER.md "Disclaimer")<br/>
[License](/./LICENSE "License")
