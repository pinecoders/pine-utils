![logo](../../images/pinelong.png "Pine")

# FAQ & Code

## Introduction

This is a compendium of frequently asked questions on Pine. Answers are short and often come with examples of code or links where more information can be found.

### Table of Contents

1. [AA](#script-structure)

## What is the variable name for the current price? 
The `close` variable holds both the price at the close of historical bars and the current price when code is running on the realtime bar.

## What’s the code for a green candle?
```
greenCandle = close>open
```

## How do I make an alert available from my indicator?
```
triggerCondition = close>close[1]
alertcondition(triggerCondition, title="Create Alert dialog box name", message="Text sent with alert.")
```
When you need to create multiple alerts you can repeat the method above for every alert you want your indicator to generate, but you can also use the method shown in [this indicator](https://www.tradingview.com/script/8AUuFonD-5-MAs-w-alerts-LucF/). Here, all the different alert conditions are bunched up in one `alertcondition()` statement. In this case, you must provide the means for users to first select which conditions will trigger the alert in the *Inputs* dialog box. When all the required conditions are selected, the user creates an alert using the only alert this indicator makes available, but since TradingView remembers the state of the *Inputs* when creating an alert, only the selected conditions will trigger the alert once it’s created, even if Inputs selections are modified by the user after the alert is created.

When more than one condition can trigger a single alert, you will most probably need to have visual cues for each condition so that when users bring up a chart on which an alert triggered they can figure out which condition caused the alert to trigger. This is a method that allows users of your script to customize the alert to their needs.

When TradingView creates an alert, it saves a snapshot of the environment that will enable the alert to run on the servers. The important elements saved with an alert are:
- Current symbol,
- Current time frame (interval),
- State of the scipt's Inputs selections,
- Current version of the script. Subsequent updates to the script’s code will not affect the alerts created with prior versions.
Also note that alerts are not available from within strategies.
