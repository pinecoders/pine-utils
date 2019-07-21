# Pine Script Code Style Guide

## Introduction

The goal of this style guide is to present a set of best practices and style guidelines for Pine Script.
Please feel free to suggest any improvements you see fit.

### Translations
1. [TODO](#)

### Table of Contents
1. [TODO](#)

## Script Structure

The Pine compiler is not very strict on exact positioning of specific statements or compiler directives. These guidelines aim to provide a standard way of ordering elements in scripts, but many other ways are syntactically correct.

1. The first line of a script should be the `//@version=` compiler directive. While the compiler defaults to Pine version 1 when no directive is used, scripts written with version 1 of Pine should nonetheless contain the `//@version=1` on their first line.

1. **Comments** describing the script are usually placed immediately after the `@version` compiler directive.

1. The first line of Pine code should be either the `study()` or `strategy()` declaration statement.

1. The next lines should contain the scripts **inputs**.

1. The following can contain **variable declarations** and **functions** in any order required. Note that all Pine functions are declared in the script's global scope, as nested function definitions are not allowed. Concerning variable declarations, some scripts lend themselves to mass declarations and others will be more readable with a *declare as you need* style that distributes declarations with the code where they are used. It's up to each coder to adopt the most useful style.

1. The rest of the script will contain **calculations**, followed by,

1. `plot` calls,
1. `strategy.*()` calls (for strategies), and
1. `alertcondition()` calls (for indicators)

```
//@version=3
//@author=Pinescripters

study("Averages - Pinescripters FAQ", precision=0)

// Averages - Pinescripters FAQ
//  v1.1, 2019.05.17

// Pinescripters is the most active community of Pine scripters on the Planet: https://pinescripters.com
// This script is referenced from the Pinescripters FAQ & Code here: https://docs.google.com/document/d/14KPvHAIIrhbupxg85GgDsupozSrX-cao7pjJz7WaBvg/edit?usp=sharing
// This script's page on TradingView: https://www.tradingview.com/script/isSfahiX-Averages-Pinescripters-FAQ/

// The script calculates:
//      1. The running average (arithmetic mean) of all up volumes,
//      2. The average of last x occurrences of up volume,
//      3. The average up volume occurrences in last y bars.
// We will use functions to calculate cases 2 and 3.
// Use the Data Window to inspect the script's values!

// Condition on which we will add to cumulative totals to build an average.
upBar = close>open


// ————— Case 1. The running average of all up volumes.
// Initialize and update cumulative total every time condition is true.
// If condition is false, then propagate previous total.
cumTotal1 = 0.0
cumTotal1 := upBar ? nz(cumTotal1[1])+volume : nz(cumTotal1[1])
// Initialize and update running count of occurrences of condition being true.
// If condition is false, then propagate previous count.
cumCount1 = 0
cumCount1 := upBar ? nz(cumCount1[1])+1 : nz(cumCount1[1])
// Calculate and plot average.
average1 = cumTotal1/cumCount1
plot(average1, "Case 1 Average", gray)
// Plot other numbers in Indicator values and Data Window only.
// [Notice that with the plotchar() statement we need to declare the color explicitly as the 3rd parameter (location=) isn't used.] 
plotchar(cumTotal1, "Case 1 Total", "", color=aqua)
plotchar(cumCount1, "Case 1 Count", "", color=aqua)


// ————— Case 2. The average of last x occurrences of up volume.
x = input(20, "Case 2: Average this many last occurrences")
avgWhenLast(_src, _cond, _cnt) =>
    // Returns average of _src for the last _cnt occurrences of _cond (lookback length = _cnt*10).
    total = 0.0
    count = 0
    // Since we don't know how many bars we must go back to find the x occurrences we need,
    // we use x*10 as the lookback upper bound, hoping we can find what we need in those bars.
    // This will generate a runtime error if x is too high.
    for i=0 to _cnt*10
        if _cond[i]
            // We found an occurrence, increment count and add volume to total.
            count := count + 1
            total := total + _src[i]
        if count==x
            // We've reached our count, exit loop.
            break
    // Calculate average. If we haven't found the required number of occurrences, set to na.
    average = count==_cnt ? total/_cnt : na

plot(avgWhenLast(volume, upBar, x), "Case 2 Average", fuchsia)


// ————— Case 3. The average up volume occurrences in last y bars.
y = input(20, "Case 3: Average all occurrences in these last bars")
avgWhenInLast(_src, _cond, _cnt) =>
    // Returns average of _src when _cond in last _cnt bars.
    total = 0.0
    count = 0
    for i=0 to _cnt-1
        if _cond[i]
            // We found an occurrence, increment count and add volume to total.
            count := count + 1
            total := total + _src[i]
    // Calculate average.
    average = total/count

plot(avgWhenInLast(volume, upBar, y), " Case 3 Average", orange)

```
## Naming Conventions

### Variable and function names

CamelCase is recommmended. Example: `emaLength`, `obLevel`, `showSignal2`, `aLongVariableName`.

### Function Parameter Names

Function parameters should be prefixed with the underscore in order to diffentiate them from global and local scope variables. Example:
```
daysInMonth( _year, _month) =>
```

### Local Scope Variable Names

[TODO-Luc](#) Need something here, imo, to prevent inadvertent confusion with global scope vars. 

**[Back to top](#table-of-contents)**
