---
layout: posts
title: The Basics of Cryptocurrency Arbitrage

#image: /assets/img/cmcBTC2.jpg 
gallery2:
  - url: /assets/img/cmcBTC2.jpg 
    image_path: /assets/img/cmcBTC2.jpg 
    alt: "placeholder image 1"
    title: "BTC"
---
___


## Motivation for this post

This post is purely for fun and for sharing some ideas I have had about this space. Many have given up on cryptocurrency since the end of 2018 when the price of BTC began falling from its peak of nearly $20,000. Today BTC is down to $4,060, trade volumes have dropped, and the subreddits have become stale and inactive. Perhaps one day the interest in this subject will return and all of this will have reversed. In that case, it can be useful to understand how arbitrage works. I have written a cryptocurrency bot in python to trade for profit and thought I would share what I know. 

{% include gallery id="gallery2" caption="The gradual fall of bitcoin value from January 2018 to March 2019. [coinmarketcap.com](https://coinmarketcap.com/)" %}


## What is arbitrage?

If you haven't heard about arbitrage, it's quite simple. Arbitrage is the buying and selling of an asset while taking advantage of the differing prices on the market. For example, many people buy items on craigslist to resell on ebay. The reason this works well for many, is because ebay is a much larger market(which theoretically leads to fairer prices on average). This means that finding a good deal on a popular item on craigslist will often result in a profit on ebay. 

For a cryptocurrency, the process goes like this. 

* Buy some cryptocurrency
* Move it to another exchange
* Sell it for a slight profit

Coinmarketcap keeps a list of all of the reasonably large cryptocurrencies as well as their values on a large list of exchanges online.  [coinmarketcap.com](https://coinmarketcap.com/) 

Examples: [Nano](https://coinmarketcap.com/currencies/nano/#markets), [Bitcoin](https://coinmarketcap.com/currencies/bitcoin/#markets), [Ethereum](https://coinmarketcap.com/currencies/ethereum/#markets)

## Why do the values of each cryptocurrency fluctuate?

Supply and demand. When a coin is being bought more than it is sold, the value starts to rise. The opposite is true when it is sold more than it is bought. 

The amount of fluctuation depends on the exchange volume. On a large exchange, the fluctuation is very little because large volumes are being bought and sold which means that its value is well represented. However, on a smaller exchange some coins can vary by up to 8% from a single relatively large buy or sell which opens up opportunities for arbitrage.

## Cryptocurrency Arbitrage Problems

In my previous example using ebay and craigslist, there is cost for shipping and driving the package to UPS for dropoff that must be factored into the equation. For cryptocurrency, it is trivial to find buyers and sellers. However, there are some hurdles involved in cryptocurrency arbitrage that are unique to the space.

There are three main hurdles to consider: 

**1.** Exchanges charge a rate for trading cryptocurrency. Trading fees generally vary between free and .2% of the trade. 

**2.** Although large exchanges in my experience haven't charged for transfer, smaller exchanges often charge a flat rate to transfer currency no matter how much cryptocurrency you move. 

**3.** Most importantly in most cases, it can take a significant amount of time(over an hour) for the first exchange to move the currency over to the second exchange. 

Note: It is possible to find exchanges where trades and transfers are free. However, for coins like BTC, LTC, and ETH the time to move currency between exchanges will always be an issue. 

## Getting around #3

One method for getting around **3** is to trade your slow coin(BTC for example) into a faster moving coin(NANO) and move the NANO instead of the BTC. In this example, you still have to worry about problem **1** and **2** but at least you can get the funds to transfer more quickly. However, **3** is still dependent on the exchange becuase although the coin may be nearly instant, some exchanges wait on the backend for a period of time before initiating the transfer. This means it could still save five to ten minutes for the transfer to occur, which can often wipe out the profits in the process. 

## Final thoughts 

There are methods which are faster than the one mentioned above. It is possible to realize profits for a coin like BTC nearly instantly. Can you think of a superior method? What kinds of problems arise with your solution?

## Like this post?

If you would like to know more, feel free to reach out over twitter. I would like to make a follow up post for this topic as there is much to talk about. 


[mm]: https://guides.github.com/features/mastering-markdown/
[ksyn]: https://kramdown.gettalong.org/syntax.html
[ksyntab]:https://kramdown.gettalong.org/syntax.html#tables
[ksynmath]: https://kramdown.gettalong.org/syntax.html#math-blocks
[katex]: https://khan.github.io/KaTeX/
[rtable]: https://dbushell.com/2016/03/04/css-only-responsive-tables/
