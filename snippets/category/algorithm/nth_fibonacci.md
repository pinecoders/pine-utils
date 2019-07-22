# Function to find Nth fibonacci

#### Snippet Description:

Function to find the sequence value of the Nth fibonacci number.

references:
* [link1](https://www.geeksforgeeks.org/program-for-nth-fibonacci-number/ "Multiple Methods:")


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


Find the input index value in the fibonacci sequence, <br/>
00 01 02 03 04 05 06 07 08 09 \[10] 11 ... <br/>
00 01 01 02 03 05 08 13 21 34 \[55] 89 ...

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

int index = input(10)
int nth = f_n_fib(index)
plot(nth)
```

