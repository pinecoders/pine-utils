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

1. The next lines should contain the script's **inputs**.

1. The following can contain **variable declarations** and **functions** in any order required. Note that all Pine functions are declared in the script's global scope, as nested function definitions are not allowed. Concerning variable declarations, some scripts lend themselves to mass declarations and others will be more readable with a *declare as you need* style that distributes declarations with the code where they are used. It's up to each coder to adopt the most useful style.

1. The rest of the script will contain **calculations**, followed by,

1. `plot` calls,
1. `strategy.*()` calls (for strategies) and,
1. `alertcondition()` calls (for indicators).

Here is an example of a complete script:

```
code
```
## Naming Conventions

### Variable and Function Names

CamelCase is recommmended. Example: `emaLength`, `obLevel`, `showSignal2`, `aLongVariableName`.

### Function Parameter Names

Function parameters should be prefixed with the underscore in order to diffentiate them from global and local scope variables. Example:
```
daysInMonth( _year, _month) =>
```

### Local Scope Variable Names

Need something here, imo, to prevent inadvertent confusion with global scope vars. 

**[Back to top](#table-of-contents)**

#TODO

- [ ] Code example in Structure
- [x] Decision on local block (for functions only?) var naming convention.


