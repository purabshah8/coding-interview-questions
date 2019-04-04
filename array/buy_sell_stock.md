# Buy and Sell Stock Problems

## Problem 1

Say you have an array for which the i-th element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

Note: You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

### Approaches

Approach 1
Buy stock today if price increases tomorrow, sell stock if price decreases tomorrow; Hold otherwise.

Approach 2
Find difference between prices today and tomorrow. If diff > 0, add to profit. Otherwise do nothing.

### Solutions

Time Complexity: O(n)

Space Complexity: O(1)

Ruby

```ruby
def max_profit(prices)
    buy_price = nil
    yday_price = prices[0]
    profit = 0
    prices.each_with_index do |price, i|
        next if i == 0
        price_diff = price - yday_price
        if not buy_price and (price_diff > 0)
            # buy stock
            buy_price = yday_price
            # net_earnings_if_sold = price - buy_price
        elsif buy_price and price_diff < 0
            # sell stock
            profit += (yday_price - buy_price)
            buy_price = nil
        end
        yday_price = price
    end
    if buy_price
        profit += (prices[-1] - buy_price)
    end
    profit
end
```

JavaScript

```js

function maxProfit(prices) {
    let buyPrice = null;
    let ydayPrice = prices[0];
    let profit = 0;
    for (let i = 1; i < prices.length; i++) {
        let priceDiff = prices[i] - ydayPrice;
        if (!buyPrice && priceDiff > 0)
            buyPrice = ydayPrice;
        else if (buyPrice && priceDiff > 0) {
            profit += (ydayPrice - buyPrice);
            buyPrice = nil;
        }
        ydayPrice = prices[i];
    }
    if (buyPrice)
        profit += prices[prices.length-1] - buyPrice;
    return profit;
}
```

```ruby
def max_profit(prices)
    profit = 0
    (prices.length-1).times do |i|
        diff = prices[i+1] - prices[i]
        profit += diff if diff > 0
    end
    profit
end
```

```js
function maxProfit(prices) {
    let profit = 0;
    for (let i = 0; i < prices.length-1; i++) {
        let priceDiff = prices[i+1] - prices[i];
        if (priceDiff > 0)
            profit += priceDiff;
    }
    return profit;
}
```

## Problem 2

Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.

### Approaches

**Brute force**: Check out the profit at all possible buy & sell dates, nested looping through array. Save and return largest found profit value


**Single Pass**: Have a max profit and a running profit variable. Loop through array, add diff between current and next to profit. If profit > max profit, set that to be new max profit. Reset profit to 0 if profit < 0. Return max profit

### Solutions

**Brute Force**

Time Complexity: O(n^2)

Space Complexity: O(1)

```ruby
def max_profit(prices)
    max_profit = 0
    prices.each_index do |i|
        (i+1...prices.length).each do |j|
            profit = prices[j] - prices[i]
            max_profit = profit if profit > max_profit
        end
    end
    max_profit
end
```
**Single Pass**

Time Complexity: O(n)

Space Complexity: O(1)

```ruby
def max_profit(prices)
    max_profit = 0
    profit = 0
    (prices.length-1).times do |i|
        profit += prices[i+1] - prices[i]
        profit = [0, profit].max # profit = 0 if profit < 0
        max_profit = [max_profit, profit].max # max_profit = profit if profit > max_profit
    end
    max_profit
end
```

```js
function maxProfit(prices) {
    let maxProfit = 0;
    let profit = 0;
    for (let i = 0; i < prices.length-1; i++) {
        profit += prices[i+1] - prices[i];
        if (profit < 0)
            profit = 0;
        if (maxProfit < profit)
            maxProfit = profit;
    }
    return maxProfit;
}
```