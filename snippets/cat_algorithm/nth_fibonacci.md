
//-----------------
//Binet's Formula to solve the Nth Fibonacci Number
f_n_fib(_step) =>
    _phi = 1.618
    _n_phi = 1/_phi
    _return = round(_step >= 0 ? pow(_phi, _step) / sqrt(5) : pow(-_n_phi, _step) / sqrt(5))
//-----------------
