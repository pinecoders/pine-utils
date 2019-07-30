![logo](../../images/pinelong.png "Pine")

# Learning Pine Roadmap

## Introduction

This document presents a path that newcomers to the Pine Script programming language can follow.

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

1. If you are interested in learning the new version 4 of Pine just released, see the Pine v4 Documentation and Pine v4 Reference Manual.
1. Kodify.net has a good TradingView blog with many useful articles on Pine programming. Subjects are explored in quite a bit of detail.
1. Backtest Rookies also has articles on Pine. They produce quality material illustrating many of the typical things Pine coders want to do or explore.
1. YouTube has some videos by Pine coders. These are a few introductory-level ones:
How To Use Tradingview Pine Script - Introduction and its part 2. A search for pine introduction tradingview will turn up a few others and you will find links to a few youtubers producing Pine content in our Pine Resources.
1. Note that you can bring up the Reference Manual from within the Pine editor by CTRL clicking on any colored language element. In the editor, you can see a list of keyboard shortcuts with Help/Pine Editor Keyboard Shortcuts. The Pine Editor's Help menu will also link you to Pine documentation.
1. PineCoders maintains a Pine FAQ & Code.

## What’s Pine?

Pine is a specialized language used to write studies (a.k.a. indicators) or backtesting strategies on the TradingView platform. Indicators are used to show graphic information on a chart or in an indicator Pane. If you wish to write a MACD in Pine, you do that by creating an indicator. Strategies can display visual information on charts or Panes in the same way an indicator would, but they also contain additional Pine commands to simulate trades in order to run backtests.

If you want to design a trading system that trades on MACD conditions, you will write a strategy to test it, and then convert it to a study to generate alerts in order to discretionary trade on them or send them to an execution bot for relaying orders to markets. Be sure to look at the XXXPineCoders Backtesting and Trading Engine if this is your goal.

Because it is specialized, Pine is very powerful. You can write two lines of Pine to do what could take hundreds in other languages. The same specialization that makes Pine powerful also implies a high abstraction level; until you understand a few key concepts about Pine and its runtime environment, it will be difficult to make sense of Pine code.

## Pine runtime environment

Pine indicator code executes once for each bar of the dataset, starting from the beginning of the chart’s history. When the realtime bar is reached, code executes every time price changes.

## Series

Most data in Pine is stored in series (somewhat like arrays, but with a dynamic index). Let’s see how the index is dynamic, and why series are also very different from arrays. In Pine, the close variable holds the price at the close of the current bar. If your code is now executing on the third bar of the dataset, close will contain the price at the close of that bar, close[1] will contain the price at the close of the preceding bar (the second), and close[2], the first.

When the same code is executed on the next bar, the fourth in the dataset, close will now contain the closing price of that bar, and the same close[1] used in your code will now refer to the close of the third bar. The close of the first bar in the dataset will now be close[3].

In the Pine runtime environment, as your code is executed once for each bar in the dataset, starting from the left of the chart, Pine is adding a new element in the series at index 0 and pushing the pre-existing elements in the series one index further away. Arrays, in comparison, are usually static in size and their content or indexing structure is not modified by the runtime environment. Pine series are thus different from arrays and share familiarity with them through their indexing syntax, mostly. Pine actually doesn't even support the array data structure.

Note that the close variable means something different at the current, realtime bar; it then represents the current price and will only contain the real closing price of the realtime bar the last time code is executed on that bar, and from then on, when it is referred to using an index.

Pine has a variable that keeps track of the bar count: n. On the first bar, n=0 and it increases by 1 at each new bar, so at the last bar, n is equal to the number of bars in the dataset minus one.

## New to Programming?
If you are new to programming, then you have a double learning curve to go through: learn to program and learn Pine. You will need to do your homework and spend the countless hours required to become able to convert your trading ideas into working code.

Either way, the most productive way to learn is always to start playing with real code early. Start with the examples in the next section. Make slight changes to the code and see what impact they have, and you’ll be on your way.

If you already have programming experience, learning Pine is mostly about becoming proficient in manipulating series, and then understanding the abstractions, the runtime environment and the limitations (no type-casting, for example), as the language itself is straightforward.

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
