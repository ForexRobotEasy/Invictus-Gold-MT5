# Invictus Gold MT5

This code is for a trading robot called Invictus Gold MT5, developed by the Forex Robot Easy Team. The purpose of this robot is to automate gold trading on the MetaTrader 5 platform. 

To use this code, you will need to include the necessary library 'PositionInfo.mqh'. This library provides functions for managing trading positions.

The code begins by declaring some global variables:
- `lotSize`: The initial lot size for trading.
- `stopLoss`: The stop loss level for the trades.
- `takeProfit`: The take profit level for the trades.

The main functionality of the robot is implemented in two functions: `TradeEntry` and `TradeExit`.

## TradeEntry()
This function is responsible for determining the conditions to enter a trade and executing a buy order. 

First, it retrieves the current bid and ask prices using the `SymbolInfoDouble` function. 

Then, it calculates the Bollinger Bands using the `iBands` function. Bollinger Bands are a popular technical indicator used to identify potential price reversals. 

Next, it filters out false entries by checking if the bid price is below the lower band and the ask price is above the upper band. If this condition is met, a buy order is placed using the `OrderSend` function. The order volume is set to `lotSize`, the price is set to the ask price, and the stop loss and take profit levels are calculated based on the current bid price and the `stopLoss` and `takeProfit` variables.

If the buy order is placed successfully, a message is printed to the console. Otherwise, an error message with the error code is printed.

## TradeExit()
This function is responsible for closing an open position.

First, it selects the current position using the `CPositionInfo` class and the `SelectByTicket` function. If there is an error selecting the position, an error message with the error code is printed and the function returns.

Next, it closes the position using the `Close` function. If the position is closed successfully, a message is printed to the console. Otherwise, an error message with the error code is printed.

## OnTick()
This function is the entry point of the code and is executed on every tick of the market.

It checks if there is an open position by checking if the `_Ticket` variable is not equal to 0. If there is an open position, the `TradeExit` function is executed to close the position. Otherwise, the `TradeEntry` function is executed to determine if a trade should be entered.

**Note:** This code is provided as a sample and should not be used for live trading without proper testing and modification to fit your specific trading strategy.

For detailed reviews and trading results of the Invictus Gold MT5 robot, you can visit the Forex Robot Easy website at [https://forexroboteasy.com/forex-robot-review/invictus-gold-mt5-review-advanced-gold-trading-algorithm/](https://forexroboteasy.com/forex-robot-review/invictus-gold-mt5-review-advanced-gold-trading-algorithm/). Please note that Forex Robot Easy is not the official developer of this product. To find the official developer, you can use the MQL5 platform.
