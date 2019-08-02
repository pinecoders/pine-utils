![logo](../../images/pinelong.png "Pine")

# FAQ & Code

## Introduction

This is a compendium of frequently asked questions on Pine. Answers often give code examples or link to the best sources on the subject.

### Table of Contents

- [Built-in variables](#built-in-variables)
- [Built-in functions](#built-in-functions)
- [Plotting](#plotting)
- [Indicators (a.k.a. studies)](#indicators)
- [Strategies](#strategies)
- [Alerts](#alerts)
- [Techniques](#techniques)


## BUILT-IN VARIABLES



### What is the variable name for the current price? 
The `close` variable holds both the price at the close of historical bars and the current price when an **indicator** is running on the realtime bar. If the script is a **strategy** running on the realtime bar, by default it runs only at the bar's close. If the `calc_on_every_tick` parameter of the `strategy()` declaration statement is set to `true`, the strategy will behave as an indicator and run on every price change of the realtime bar.

### What is the code for a green candle?
```
greenCandle = close > open
```
Once you have defined the `greenCandle` variable, if you wanted a boolean variable to be `true` when the 3 last candles were green ones, you could write:
```
threeGreenCandles = greenCandle and greenCandle[1] and greenCandle[2]
```
> Note that the variable name `3GreenCandles` would have caused a compilation error. It is not legal in Pine as it begins with a digit.



## BUILT-IN FUNCTIONS


### Why do I get an error message when using highest() or lowest()?
Most probably because you are trying to use a series instead of an integer as the second parameter (the length). Either use an integer or use the RicardoSantos replacements [here](https://www.tradingview.com/script/32ohT5SQ-Function-Highest-Lowest/). If you don't know Ricardo, take the time to look at his indicators while you're there. Ricardo is among the most prolific and ingenious Pinescripters out there.



## PLOTTING



### Can I plot diagonals between two points on the chart?
Yes, using the [`line.new()`](https://www.tradingview.com/pine-script-reference/v4/#fun_line{dot}new) function available in v4.

### How do I plot a support line?
To plot a continuous line in Pine, you need to either:
1. Look back into elapsed bars to find an occurrence that will return the same value over consecutive bars so you can plot it, or
1. Find levels and save them so that you can plot them. In this case your saving mechanism will determine how many levels you can save. 
These are examples of three different techniques used to determine and draw support lines:
- [Backtest Rookies](https://backtest-rookies.com/2018/10/05/tradingview-support-and-resistance-indicator/),
- [Auto-Support v 0.2 by jamc](https://www.tradingview.com/script/hBrQx1tG-Auto-Support-v-0-2/)
- [S/R Barry by likebike](https://www.tradingview.com/script/EHqtQi2g-S-R-Barry/)

### How many plots, security() calls, variables or lines of code can I use?
The limit for plots is 64. Note than one plot statement can use up more than one allowed plot, depending on how it is structured.
The limit for `security()` calls is 40.
The limit for variables is 1000.
We do not know of a limit to the number of lines in a script. There is, however a limit of 50K compiled tokens, but they don't correspond to code lines.

### How can I use colors in my indicator plots?
See [Working with colours](https://kodify.net/tradingview/colours/) by kodify.

### How do I make my indicator plot over the chart?
Use `overlay=true` in `strategy()` or `study()` declaration statement, e.g.,:
```
study("My Script", overlay=true)
```
If your indicator was already in a Pane before applying this change, you will need to use Add to Chart again for the change to become active.



## INDICATORS



### Can I create an indicator that plots like the built-in Volume or Volume Profile indicators?
No.

### How do I feed the output of one script to another script?
Use the following in your code:
```
ExternalIndicator = input(close, "External Indicator")
```
From the script's *Inputs* you will then be able to select a plot from another indicator if it present on your chart.
You can use only one such statement in your script. If you use more than one, the other indicator plots will not be visible from the *Inputs* dropdown.
You cannot use this technique in strategies.

### Can I write a script that plots like the built-in Volume Profile or Volume indicators?
No. TradingView uses special code for these that is not available to standard Pine scripts.

### How can I use one script's output as an input into another?
See how our [Signal for Backtesting-Trading Engine](https://www.tradingview.com/script/y4CvTwRo-Signal-for-Backtesting-Trading-Engine-PineCoders/) can be integrated as an input to our [Backtesting-Trading Engine](https://www.tradingview.com/script/dYqL95JB-Backtesting-Trading-Engine-PineCoders/).


## STRATEGIES



### How do I implement date range filtering in strategies?
```
DateFilter = input(false, "═════════════ Date Range Filtering")
FromYear = input(1900, "From Year", minval=1900)
FromMonth = input(1, "From Month", minval=1, maxval=12)
FromDay = input(1, "From Day", minval=1, maxval=31)
ToYear = input(2999, "To Year", minval=1900)
ToMonth = input(1, "To Month", minval=1, maxval=12)
ToDay = input(1, "To Day", minval=1, maxval=31)
FromDate = timestamp(FromYear, FromMonth, FromDay, 00, 00)
ToDate = timestamp(ToYear, ToMonth, ToDay, 23, 59)
TradeDateIsAllowed() => DateFilter? (time >= FromDate and time <= ToDate) : true
```
You can then use the result of `TradeDateIsAllowed()` to confirm your entries using something like this:
```
EnterLong = GoLong and TradeDateIsAllowed()
```
> Note that with this code snippet, date filtering can be enabled/disabled using a checkbox. This way you don't have to reset dates when filtering is no longer needed; just uncheck the box.

### How do I write code for a signal with 2 conditions that occur at different times?
Backtest Rookies has a [blog post](https://backtest-rookies.com/2018/10/26/tradingview-opening-a-window/) on the subject.

### How can I save the entry price in a strategy?
See [How to Plot Entry Price](https://www.tradingview.com/script/bHTnipgY-HOWTO-Plot-Entry-Price/) by vitvlkv

### How do I convert a strategy to a study in order to generate alerts for discretionary trading or a third-party execution app/bot?
The best way to go about this is to write your strategies in such a way that their behavior depends the least possible on `strategy.*` variables and `strategy.*()` call parameters, because these cannot be converted into an indicator.

The PineCoders [Backtesting-Trading Engine](https://www.tradingview.com/script/dYqL95JB-Backtesting-Trading-Engine-PineCoders/) is a framework that allows you to easily convert betweeen strategy and indicator modes because it manages trades using custom Pine code that does not depend on an involved setup of `strategy.*()` call parameters.



## ALERTS



### How do I make an alert available from my indicator?
Two steps are required:
1. Insert an `alertcondition()` call in an indicator script.
2. Create an alert from the TV Web user interface (ALT-A) and choose the script's alert condition.

See the User Manual page on [`alertcondition()`](https://www.tradingview.com/pine-script-docs/en/v4/annotations/Alert_conditions.html). Code to create an alert condition looks like:
```
triggerCondition = close > close[1]
alertcondition(triggerCondition, title = "Create Alert dialog box name", message = "Text sent with alert.")
```
When you need to create multiple alerts you can repeat the method above for every alert you want your indicator to generate, but you can also use the method shown in [this indicator](https://www.tradingview.com/script/8AUuFonD-5-MAs-w-alerts-LucF/). Here, all the different alert conditions are bunched up in one `alertcondition()` statement. In this case, you must provide the means for users to first select which conditions will trigger the alert in the *Inputs* dialog box. When all the required conditions are selected, the user creates an alert using the only alert this indicator makes available, but since TradingView remembers the state of the *Inputs* when creating an alert, only the selected conditions will trigger the alert once it’s created, even if *Inputs* selections are modified by the user after the alert is created.

When more than one condition can trigger a single alert, you will most probably need to have visual cues for each condition so that when users bring up a chart on which an alert triggered they can figure out which condition caused the alert to trigger. This is a method that allows users of your script to customize the alert to their needs.

When TradingView creates an alert, it saves a snapshot of the environment that will enable the alert to run on the servers. The elements saved with an alert are:
- Current symbol,
- Current time frame,
- State of the script's *Inputs* selections,
- Current version of the script. Subsequent updates to the script’s code will not affect the alerts created with prior versions.

> Note that while alert condition code will compile in strategy scripts, they are only functional in studies.

### I have a custom script that generates alerts. How do I run it on many symbols?
You need to create a separate alert for each symbol. There is currently no way to create an alert for all the symbols in a watchlist or for the Screener.

If one of the generic indicators supplied with the Screener suits your needs and your symbols are tagged with a color label, you can create an alert on those markets from within the Screener.



## TECHNIQUES



### How do I save a value or state for later use?
Backtest Rookies has a [blog post](https://backtest-rookies.com/2018/11/23/tradingview-save-a-variable-store-a-value-for-later/) on the subject.
Pine Example: [Holding a state in a variable](https://www.tradingview.com/script/llcoIPKG-Pine-Example-Holding-a-state-in-a-variable/) by vitvlkv.

### How do I calculate averages?
1. If you just want the average between two values, you can use `avg(val1, val2)` or `(val1 + val2)/2`.
1. To average the last x values in a series, you can use `sma(series, x)`.

### How can I calculate averages only when a condition is true?
[This script](https://www.tradingview.com/script/isSfahiX-Averages-PineCoders-FAQ/) shows how to calculate a conditional average using three different methods.

