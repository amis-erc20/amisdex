---
layout: post
title: How AMIS Exchange compares to other exchanges
tags: [industry]
---

> This post was originally written by <a href="https://www.linkedin.com/in/kieranelby/" target="\_blank">Kieran Elby</a> for a project he has since shut down. We have made some small modifications to reference Ubitok.io as AMIS Exchange would not exist otherwise, but almost all credit for this article belongs to Kieran.

One question we are often asked is how AMIS Exchange compares to other exchanges - particularly to the decentralized EtherDelta, or to the exchange protocol 0x, or to centralized exchanges like GDAX or Poloniex.

Our main differentiator is that AMIS Exchange is (so far) the *only* exchange to offer a limit order book with best execution matching entirely on-chain.

Best execution matching of limit orders gives clients a modern trading experience, like one would expect on a centralized exchange.

Being entirely on-chain means AMIS Exchange cannot be shutdown or your funds taken - not even by its creators - as long as the Ethereum network keeps functioning.

When we looked around before building AMIS DEX Exchange, we found other decentralized exchanges tend to compromise.

Either they use an off-chain matching engine (meaning they are still vulnerable to downtime or regulatory action),
or they offer a much poorer trading experience than a traditional exchange. Or, in some cases, both of those!

As always, these things are a bit subjective, but we've tried to capture the strengths and weaknesses of the various exchanges below:

|Rating|AMIS Exchange|EtherDelta|0x Relayers|Centralized Exchanges|
|--|--|--|--|--|
|Unstoppability|![happy](../img/happy.png)|![meh](../img/meh.png)|![sad](../img/meh.png)|![sad](../img/sad.png)|
|Order Execution|![happy](../img/happy.png)|![sad](../img/sad.png)|![sad](../img/sad.png)|![happy](../img/happy.png)|
|Deposit/Withdrawal Limits|![happy](../img/happy.png)|![happy](../img/happy.png)|![happy](../img/happy.png)|![sad](../img/sad.png)|
|Gas Costs for Adding Orders|![sad](../img/sad.png)|![happy](../img/happy.png)|![happy](../img/happy.png)|![happy](../img/happy.png)|
|Trading Fees|![happy](../img/happy.png)|![meh](../img/meh.png)|![happy](../img/happy.png)|![meh](../img/meh.png)|
|Transparency and Fairness|![happy](../img/happy.png)|![meh](../img/meh.png)|![meh](../img/meh.png)|![sad](../img/sad.png)|
|High Frequency Trading|![sad](../img/sad.png)|![meh](../img/meh.png)|![meh](../img/meh.png)|![happy](../img/happy.png)|
|User Experience|![meh](../img/meh.png)|![sad](../img/sad.png)|![meh](../img/meh.png)|![happy](../img/happy.png)|
|Smart Contract Clients|![happy](../img/happy.png)|![meh](../img/meh.png)|![sad](../img/meh.png)|![sad](../img/sad.png)|

Here's a few notes on some of the ratings above ...

### Unstoppability

This is AMIS DEX Exchange's UNIQUE selling point!

We're big fans of EtherDelta and 0x relays, but it's not quite as decentralized as often thought - the order book is held on EtherDelta's servers, making it somewhat vulnerable to being shutdown due to regulatory action or DDOS attack.

Similar comments apply to 0x relayers. On the other hand, clients' coins are safely protected by a smart contract in both cases, which is a big plus.

Unsurprisingly, centralized exchanges come out worse since not only are they a single point of failure, clients have to trust them not to run off with their funds.

### Order Execution

On both EtherDelta and 0x relayers, clients have to pick one single resting order
to trade against (and hope no-one else gets there first!).

AMIS Exchange offers a more modern trading experience where clients place limit orders which can match several resting orders according to price-time priority, giving clients best execution.

Like centralized exchanges, AMIS Exchange supports various order types including maker-only and IoC orders.

### Deposit/Withdrawal Limits

Here the decentralized exchanges win - clients do not lose control of their coins and are not prevented from moving their coins around.

### Gas Costs for Adding Orders

This is where AMIS Exchange currently suffers, particularly for smaller orders and volatile markets - because everything happens on-chain, placing orders costs gas, even if they don't get matched.

We're confident though that the Ethereum Foundation and other Ethereum developers will make Ethereum transactions faster, cheaper, and more scalable - making this less and less of a problem.

### Trading Fees

- AMIS Exchange - 0.2% on liquidity taken (applied per order)
- EtherDelta - 0.30% on liquidity taken (applied per order)
- 0x - relayer fees are a bit of an unknown at the time of writing
- Centralized exchanges - typically up to 0.20% on trades depending on monthly volume

### Transparency and Fairness

AMIS Exchange does well here - all our source code can be examined on github, and the smart contract enforces price-time priority for orders. There's no special treatment for preferred clients or any way to spoof orders that aren't backed by real funds. AMIS Exchange is somewhat reliant on the fairness of the Ethereum miners though.

EtherDelta loses out a little here for not making source available for their user interface or their order book maintenance code. It is somewhat vulnerable to market abuse such as spoofing, since clients can place more orders into the book than they have funds to cover.

The 0x protocol is commendably open, but there are some question marks around how unfair practices such as spoofing and front-running can be prevented by relayers. Building a decentralized, trustless system is hard - that's why AMIS Exchange would rather let the Etherum Foundation do that, instead of inventing a new protocol layer above it.

Centralized exchanges tend to be rather secretive about how they operate, and certainly there have been cases of centralized exchanges reporting inflated trading volumes and giving certain clients preferential access.

### High Frequency Trading and User Experience

Centralized exchanges have an inherent advantage in both areas for the same reason - they have all the market information in a consistent state in one place and can update and query it much faster than is possible in a decentralized system.

### Smart Contract Clients

Whether smart contracts making trades will ever be a large part of the market remains to be seen - but AMIS Exchange is one of the few venues where an Ethereum smart contract can place orders directly into an order book. A use-case might be an ICO contract running an auction.

### Competition

See MKR, DAI on Oasis.

### And finally

We think there's a place in the market for many different exchanges to exist - they all have strengths in different areas. We hope this article helps you find the right exchange for your trading!
