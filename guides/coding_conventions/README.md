
![logo](../../images/pinelong.png "Pine")

# Pine Script Coding Conventions

## Introduction

The goal of these Coding Conventions is to present a set of best practices and style guidelines for Pine Script. By making Pine scripts easier to read, these guidelines make open source code more usable, while also providing safeguards that minimize the risk of errors for developers.

### Table of Contents

1. [Script Structure](#script-structure)
1. [Naming Conventions](#naming-conventions)
1. [Spacing](#spacing)
1. [Line Wrapping](#line-wrapping)

## Script Structure

The Pine compiler is not very strict on exact positioning of specific statements or compiler directives. While many other arrangements are syntactically correct, these guidelines aim to provide a standard way of ordering elements in scripts:

1. The first line of a script should be the `//@version=X` compiler directive, where `X` is replaced by the version of Pine the script is written for. While the compiler defaults to Pine version 1 when no directive is used, scripts written using version 1 of Pine should nonetheless contain the `//@version=1` directive on their first line.

1. **Comments** describing the script are usually placed immediately after the `@version` compiler directive.

1. The first Pine statement in the script should be either the `study()` or `strategy()` declaration statement.

1. The next lines should contain the script's **inputs**.

1. The following lines can contain **variable initializations** and **function definitions** in any order required. Note that all Pine functions must be defined in the script's global scope, as nested function definitions are not allowed. Concerning variable initializations, some scripts lend themselves to mass initializations and others will be more readable with an *initialize as you need* style that places initializations with the code segments where the variables are used. It's up to each coder to adopt the most useful style. Local block variables must be declared in the local block where they will be used.

1. The rest of the script will contain **calculations**, followed by,

1. `plot()` calls,
1. `strategy.*()` calls (for strategies) and,
1. `alertcondition()` calls (for indicators), if needed.

Here is an example of a complete script:

```
//@version=4
// MACD indicator, a Gerald Appel concept.
// Author: PineCoders, v1.0, 2019.07.31
study("MACD")

// ————— Inputs
fast = input(12, "Fast Length")
// Calculates slow length from fast length and normalizes it if needed.
f_getSlowLength(_len) =>
    _tempLen = _len * 2
    if _tempLen < 20 or _tempLen > 30
        _tempLen := 25
    _tempLen
slow = f_getSlowLength(fast)

// ————— Calculations
fastMa = ema(close, fast)
slowMa = ema(close, slow)
macd = fastMa - slowMa
signal = sma(macd, 9)

// ————— Plots
plot(macd, color=color.blue)
plot(signal, color=color.orange)
```

**[Back to top](#table-of-contents)**

## Naming Conventions

### Variable Names

We recommend using CamelCase for variable names. Example: `emaLength`, `obLevel`, `showSignal2`, `aLongVariableName`.

### Function Names

For function names, we recommend using a Hungarian-style `f_` prefix in combination with the usual CamelCase. The `f_` prefix guarantees disambiguation between user-defined and built-in functions. Example: `f_sinh`, `f_daysInMonth`.

### Function Parameter Names

Function parameters should be prefixed with the underscore in order to differentiate them from global and local scope variables. Example:
```
daysInMonth(_year, _month) =>
```

### Function Dependencies

When a function requires global scope variables to perform its calculations, these dependencies should be documented in comments. Dependencies are to be avoided whenever possible, as they jeopardize function portability and make code more difficult to read.

```
lenMultiplier = input(2, "Length Multiplier")

f_getSlowLength(_len) =>
    // Dependencies: lenMultiplier (initialized in inputs). 
    _tempLen = _len * lenMultiplier
    if _tempLen < 20 or _tempLen > 30
        _tempLen := 25
    _tempLen
```

This is a preferable way to write the same function, which eliminates dependencies:

```
f_getSlowLength(_len, _mult) =>
    _tempLen = _len * _mult
    if _tempLen < 20 or _tempLen > 30
        _tempLen := 25
    _tempLen
```
### Local Scope Variable Names

The same underscore prefix used for function parameters should also be used for all local variables. Example:
```
f_getSlowLength(_len) =>
    _tempLen = _len * 2
    if _tempLen < 20 or _tempLen > 30
        _tempLen := 25
    _tempLen
```
```
if something
    _myLocalVar = something
```
```
for _i = 0 to 100
    _myLocalVar = something[_i]
```

**[Back to top](#table-of-contents)**

## Spacing

A space should be used on both sides of all operators, whether they be assignment, numerical (binary or unary) or logical. A space should also be used after commas. Example:

```
a = close > open ? 1 : -1
var newLen = 2
newLen := min(20, newlen + 1)
a = - b
c = d > e ? d - e : d
index = bar_index % 2 == 0 ? 1 : 2
plot(series, color = color.red)

```

## Line Wrapping

When lines need to be continued on the next, use two spaces to indent the continuation line.

**[Back to top](#table-of-contents)**



