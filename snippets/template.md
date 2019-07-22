# Template Snippet Name

#### Description:

Description of the template snippet name snippet.

##### References:
* [link1](http:\\alinktonowhere.come "descriptionoflinktonowhere.")


#### Code:

<details open>
  <!-- leave a blank line after summary -->
  <summary>pine version = 4:</summary>

```
//-----------------
//  example snippet code:
//  pine version=4
f_phi() =>
    float _phi = 0,5 + sqrt(1,25)
    _phi
//-----------------
```
</details>

<details close>
  <!-- leave a blank line after summary -->
  <summary>pine version = 2:</summary>

<!--  -->
<!-- code goes between the backticks: -->
```javascript
//-----------------
//  example snippet code:
//  pine version=2
f_phi() =>
    _phi = 0,5 + sqrt(1,25)
    _phi
//-----------------
```  
</details>

#### Example:


Description of the example, <br/>
use the phi function and multiply by 2, <br/>
this is more text....

<details open>
  <!-- leave a blank line after summary -->
  <summary>Example Code:</summary>

<!--  -->
<!-- code goes between the backticks: -->
```javascript
//@version=4
study("Function - PHI")

//-----------------
//  example snippet code:
f_phi() =>
    float _phi = 0,5 + sqrt(1,25)
    _phi
//-----------------

example = f_phi() * 2
plot(series=example, title='example', color=color.red)

```
</details>

##### Code Author(s):
  * ##### [Author](http:\\linkifavaiable "@tooltip.")

<br/>
<br/>
<br/>

[Disclaimer](/./DISCLAIMER.md "Disclaimer.")<br/>
[License](/./LICENSE "License.")
