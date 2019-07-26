
![logo](../../images/pinelong.png "Pine")

# Pine Script Coding Conventions

## Introduction

The goal of these Coding Conventions is to present a set of best practices and style guidelines for Pine Script. By making Pine scripts easier to read, these guidelines make open source code more readable, while also providing safeguards that minimize the risk of errors for developers.

### Translations

1. [TODO](#)

### Table of Contents

1. [Script Structure](#script-structure)
1. [Naming Conventions](#naming-conventions)
1. [Line Wrapping](#line-wrapping)

## Script Structure

The Pine compiler is not very strict on exact positioning of specific statements or compiler directives. These guidelines aim to provide a standard way of ordering elements in scripts, but many other ways are syntactically correct.

1. The first line of a script should be the `//@version=` compiler directive. While the compiler defaults to Pine version 1 when no directive is used, scripts written with version 1 of Pine should nonetheless contain the `//@version=1` on their first line.

1. **Comments** describing the script are usually placed immediately after the `@version` compiler directive.

1. The first line of Pine code should be either the `study()` or `strategy()` declaration statement.

1. The next lines should contain the script's **inputs**.

1. The following can contain **variable declarations** and **functions** in any order required. Note that all Pine functions are declared in the script's global scope, as nested function definitions are not allowed. Concerning variable declarations, some scripts lend themselves to mass declarations and others will be more readable with a *declare as you need* style that distributes declarations with the code where they are used. It's up to each coder to adopt the most useful style. In any case, declare variables that will only be used in a local block in that same local block.

1. The rest of the script will contain **calculations**, followed by,

1. `plot` calls,
1. `strategy.*()` calls (for strategies) and,
1. `alertcondition()` calls (for indicators).

Here is an example of a complete script:

```
code
```

**[Back to top](#table-of-contents)**

## Naming Conventions

### Variable Names

We recommend using CamelCase used for variable names. Example: `emaLength`, `obLevel`, `showSignal2`, `aLongVariableName`.

### Function Names

For function names, we recommend using a combination of Hungarian-style `f_` prefix with the usual CamelCase. The prefix allows disambiguation between user-defined and built-in functions. Example: `f_sinh`, `f_daysInMonth`.

### Function Parameter Names

Function parameters should be prefixed with the underscore in order to differentiate them from global and local scope variables. Example:
```
daysInMonth(_year, _month) =>
```

### Local Scope Variable Names

The same underscore prefix used for function parameters should also be used for all local variables. Example:
```
f_capLength( _len)
    _tempLen = _len*20
    if _tempLen<200 or _tempLen>300
        _tempLen := 200
    _templen
```
```
if something
    _myLocalVar = something
```
```
for _i = 0 to 100
    _myLocalVar = something
```

**[Back to top](#table-of-contents)**

## Line Wrapping

When lines need to be continued on the next, use two spaces to indent the continuation line.

**[Back to top](#table-of-contents)**

# TODO

- [ ] Code example in Structure
- [ ] Decision on local block (for functions only?) var naming convention.


