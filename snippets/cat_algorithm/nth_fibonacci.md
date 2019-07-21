# Function to find Nth fibonacci

#### Snippet Description:

Function to find the sequence value of the Nth fibonacci number.


#### Code:
<!--  -->
<!-- code goes between the backticks: -->
```javascript
//-----------------
//Binet's Formula to solve the Nth Fibonacci Number
f_n_fib(_step) =>
    _phi = 1.618
    _n_phi = 1/_phi
    _return = round(_step >= 0 ? pow(_phi, _step) / sqrt(5) : pow(-_n_phi, _step) / sqrt(5))
//-----------------
```


#### Example:

in the next code it uses the function to do something with it.....

<!--  -->
<!-- code goes between the backticks: -->
```javascript
//@version=4
study(title="how to use the function:")

//-----------------
//Binet's Formula to solve the Nth Fibonacci Number
f_n_fib(_step) =>
    _phi = 1.618
    _n_phi = 1/_phi
    _return = round(_step >= 0 ? pow(_phi, _step) / sqrt(5) : pow(-_n_phi, _step) / sqrt(5))
//-----------------

plot(close)
```

