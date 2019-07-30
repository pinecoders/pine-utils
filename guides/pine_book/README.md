![logo](../../images/pinelong.png "Pine")

# Learning Pine Roadmap

## Introduction

This document presents a path that newcomers to the [Pine Script](https://www.tradingview.com/pine-script-docs/en/v4/Introduction.html) programming language can follow. Pine Script is the programming language used on the [TradingView](http://www.tradingview.com) charting platform.

### Table of Contents

1. [Where to go?](#where-to-go)
1. [What’s Pine?](#whats-Pine)
1. [Pine runtime environment](#pine-runtime-environment)
1. [Series](#series)
1. [New to programming](#new-to-programming)
1. [Code examples](#code-examples)
1. [Troubleshooting Pine code](#troubleshooting-pine-code)
1. [Conversion from other platforms](#conversion-from-other-platforms)

## Where to go?


Resources to learn Pine are distributed and there is no real Primer for Pine. Here are a few areas to explore:

1. The two primary sources of information on Pine are the [Pine v4 Documentation](https://www.tradingview.com/pine-script-docs/en/v4/Quickstart_guide.html) and [Pine v4 Reference Manual](https://www.tradingview.com/pine-script-reference/v4/).<br/>
Follow the instructions in the documentation's Quickstart Guide page to put your first script in action on a chart, and follow the links in that page to familiarize yourself with Pine's key concepts.
1. Once you start working in the Pine Editor, you can bring up the Reference Manual by CTRL-clicking on any colored language keyword. From the editor, you can also view a list of keyboard shortcuts by selecting *Pine Editor Keyboard Shortcuts* from the *Help* menu. The editor's *Help* menu will link you to v4 and v3 documentation, and to forums where you can ask questions on Pine.
1. [Kodify.net](https://kodify.net/tradingview-programming-articles/) is the largest repository of Pine-related articles out there. In more than 200 articles related to Pine programming, they explore Pine features thoroughly and also present techniques for realizing common tasks in Pine.
1. [Backtest Rookies](https://backtest-rookies.com/category/tradingview/) also has some articles on Pine. They produce quality material illustrating many of the typical things Pine coders want to do or explore.
1. YouTube has content by Pine coders. These are a few introductory-level ones:
[How To Use Tradingview Pine Script - Introduction](https://www.youtube.com/watch?v=Kwlxngw1YBY) and its [Part 2](https://www.youtube.com/watch?v=3wW10q9QDA8). A search for pine introduction tradingview will turn up a few others and you will find links to a few youtubers producing Pine content in our Pine Resources.
1. PineCoders maintains a Pine FAQ & Code.

## What’s Pine?

Pine is a specialized language used to write scripts that can take two very different forms: **studies** (a.k.a. **indicators**, as we will name them) or backtesting **strategies**. *Indicators* are used to show graphic information on a chart or in an indicator Pane. If you wish to write a MACD indicator in Pine, you do that by creating a script using the `study()` declaration statement at the beginning of the script. **Strategies** use the `strategy()` declaration statement and can display visual information on charts or Panes in the same way an indicator would, but they also contain additional Pine statements to simulate trades in order to run backtests.

If you want to design a trading system that trades on MACD setups, you may write a *strategy* to test it, and then convert it to a *study* (or *indicator*) to generate alerts in order to discretionary trade on them, or send them to a third-party execution bot for relaying orders to markets. Be sure to look at the PineCoders [Backtesting and Trading Engine](https://www.tradingview.com/script/dYqL95JB-Backtesting-Trading-Engine-Pinescripters/) if this is your objective.

Because it is specialized, Pine is very powerful. You can write two lines of Pine to do what could take hundreds in other languages. The same specialization that makes Pine powerful also implies a high abstraction level; until you understand a few key concepts about Pine and its runtime environment, it will be difficult to make sense of Pine code.

## Pine runtime environment

Pine indicator code executes once for each bar of the dataset, starting from the beginning of the chart’s history. When the realtime bar is reached, code executes every time price changes. See [here](https://www.tradingview.com/pine-script-docs/en/v4/language/Execution_model.html) for more information.

## Series

The main data type used in Pine scripts is called a series. It is a continuous list of values that stretches back in time from the current bar and where one value exists for each bar. While this structure may remind many of an array, a Pine series is totally different and thinking in terms of arrays will be detrimental to understanding this key Pine concept. You can read about series [here](https://www.tradingview.com/pine-script-docs/en/v4/language/Type_system.html#series) and get more information on how to use them [here](https://www.tradingview.com/pine-script-docs/en/v4/language/Operators.html#history-referencing-operator).<br/>
— quoted from the Pine v4 documentation

## New to Programming?
If you are new to programming, then you have a double learning curve to go through: learn to program and learn Pine. You will need to do your homework and spend the countless hours required to become able to convert your trading ideas into working code.

Either way, the most productive way to learn is always to start playing with real code early. Start with the examples in the next section. Make slight changes to the code and see what impact they have, and you’ll be on your way.

If you already have programming experience, learning Pine is mostly about becoming proficient in manipulating series, and then understanding the abstractions, the runtime environment and the typing and runtime limitations, as the language itself is straightforward.

## Code examples

- TradingView Pine v4 example of a simple script.
- PineCoders publishes Pine examples and tools on TradingView.
- This is a Kodify article on Pine operators.
- Backtest Rookies has an article on Writing a First Script.
- Examples of common tasks in Pine by vtvlkv.

## Troubleshooting Pine code

Here are a few methods for troubleshooting pine-related issues:
Google is sometimes helpful. You'll often end up on either kodify.net, backtestrookies.com, stackoverflow.com, getsatisfaction.com or the TV wiki.

The are tens of thousands of scripts published on TradingView, many with open source code. To find them:

1. Search TV scripts by going to TradingView’s main page, selecting Scripts in the dropdown at the left of the search field and entering what you are looking for.
For better search results, use Google with:
site:tradingview.com intitle:indicatorname
1. Use the Telegram search function to search the XXXPineCoders group for your issue. Countless problems have been discussed—and many resolved—in the past.
1. Search Pastebin with keyword version=3 and what you are looking for.
1. Plot the hell out of it. Try simple temporary plots of data, just to see where you're at. It’s a good way to get a feel for what's going on inside the runtime loop. If your debugging plots wreak havoc on scale when you plot(var), use plotchar(var, "Description", "") to plot the value in the indicator values and in the Data Window (look it up; it's real useful) without disrupting the visuals on your indicator. Backtest Rookies has an article on debugging techniques.
1. Ask questions in either the TradingView Pine Script Editor chat, at XXXPineCoders, or StackOverflow. When you ask questions, take the time to state your problem concisely and clearly. The better you explain it, the more chances you have of getting an answer. The people answering questions in the different groups will not teach you Pine; you need to learn on your own as we’ve all done, but they can help you out when you are stuck.

## Conversion from other platforms

The TradingView platform does not run indicators written for other platforms. They will require conversion in Pine before they can run on TradingView charts.
