## Pine Script Code Style Guide

### Introduction

The goal of this style guide is to present a set of best practices and style guidelines for Pine Script. Please feel free to suggest any improvements you see fit.

### Translations
1. [TODO](#)

### Table of Contents
1. [TODO](#)

### Script Structure

The Pine compiler is not very fussy on exact positioning of specific statements or compiler directives. These guidelines aim to provide a standard way of ordering elements in scripts, but many other ways are syntactically correct.

The first line of a script should be the `//@version=` compiler directive. While the compiler defaults to Pine version 1 when no directive is used, scripts written with version 1 of Pine should nonetheless contain the `//@version=1` on their first line.

Comments describing the script are usually place immediately after the `@version` compiler directive.

The first line of Pine code should be either the `study()` or `strategy()` declaration statement.

The next lines should contain the scripts inputs.

The following can contain variable declarations and functions in any order required. Note that all Pine functions are declared in the script's global scope, as nested function definitions are not allowed. Concerning variable declarations, some scripts lend themselves to mass declarations and others will be more readable with a *declare as you need* style that distributes declarations with the code where they are used. It's up to each coder to adopt the most useful style.

The rest of the script will contain calculations, which will typically be followed by:

- plot calls,
- `strategy.*()` calls (for strategies),
- `alertcondition()` calls (for indicators)


**[Back to top](#table-of-contents)**
