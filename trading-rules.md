---
layout: page
title: Trading Rules Guidelines
subtitle: we suggest reading these before trading on AMIS Exchange
---

The scope of this document is to provide service operation guidelines when interfacing with the UI and the On chain orderbook smart contract; it explains the types of orders offered by AMIS Dex Exchange, the trading rules,  the operational lifecycle model, the fee structure, order limits, followed by the terms and conditions. See table of content below:

## Table of Contents
- [Limit Orders](#limitorders)
- [Market Orders and Stop Orders](#marketordersandstoporders)
- [Order Specification](#orderspecification)
- [Gas Costs](#gastcost)
- [Gas Top Up](#gastopup)
- [Fees](#fees)
- [Gas Cost per txs type Summary](#gascostpertxstypesummary)
- [Order Lifecycle](#orderlifecycle)
- [Confirmations, Forks, and Orphaned Transactions](#Confirmations, Forks, and Orphaned Transactions)
- [Smart contract release](#smartcontractrelease)
- [Marketplace participants](#marketplaceparticipants)
- [Terms and conditions](#termsandconditions)

## Limit Orders

AMIS Exchange uses Limit Orders to ensure you get a fair price.

A Limit Order lets you set your own price when buying or selling.

AMIS Exchange guarantees Best Execution - for example, if you enter an order to buy at a price of 1.30, and there's an existing order in the book to sell at 1.25, you'll get the better (for you) price of 1.25. If your order matches several resting orders in the book, price-time priority is applied to decide which orders get matched first.

The size of the order is always specified in the base currency internally (whether buying or selling). For example, on an AMIS/ETH book where AMIS tokens are being bought and sold for Ether, you would enter the number of AMIS tokens you want to buy or sell.

Most limit orders can be partially filled - this can happen if, say, you enter an order to buy 10,000 AMIS but only 4,000 AMIS are available at the price you want.

## Market Orders and Stop Orders

Because the time taken to get the transaction containing your order into the Ethereum blockchain can vary considerably, we feel Market Orders are too dangerous and do not support them. We suggest using an Immediate or Cancel Limit Order with a generous price instead.

We do not currently support Stop Orders (one difficulty is how to pay the gas to trigger the order when the stop is reached), but are keen to offer them (as Stop-Limit orders) in future.

## Order Specification

AMIS Exchange supports the following Order specification for your maker/taker orders, which let you control the conditions under which your order can or cannot be filled:

|Good Till Cancel| - Your order will be matched against existing orders. If it cannot be completely filled, the remaining unfilled portion of your order will be added to the book and remain valid until you cancel it. These are the default terms.|
|Immediate or Cancel| - Your order will be matched against existing orders. If it cannot be completely filled, the remaining unfilled portion will be cancelled. The order will never be added to the book. Popular for quick, small trades.|
|Maker Only| - Your order will be rejected immediately (without matching) if any part of it would be filled. Otherwise, it will be added to the book and remain valid until you cancel it. Popular with market makers. Also known as Post Only.|

Some exchanges (Bittrex) call these the Time in Force of the order.

## Gas Costs

AMIS Exchange performs all matching using a smart contract running on the Ethereum blockchain. This is good - it means you don't need to worry about our servers failing, being shutdown or being hacked.

However, one downside is that running code on the Ethereum blockchain is slow and expensive - every operation costs "gas", which is paid for by the user via their Ethereum wallet. This helps keep the network running - thousands of nodes all need to agree on the results.

We've done our best to keep gas usage of our smart contract as low as possible. It can still use a lot of gas if you place an order that matches a large number of resting orders on the book.

For example, if the book contains a hundred different open orders to sell 1 AMIS token each @ 2.0, and you place an order to buy 100 AMIS @ 2.0, your order will match those other 100 orders - that's 101 clients who need to be paid.

To let you stay in control of gas costs (and avoid running out of gas), we limit the number of matches allowed when placing a new order (there's no limit for orders already in the book). It works like this:

|Immediate or Cancel orders|The remaining unfilled portion of the order is cancelled if the limit is reached|
|Maker Only orders|No limit applied - they're always rejected if they would match an order|
|Good Till Cancel orders|You can choose what to do if the maximum number of matches is reached - see Gas Top Up section.|

Most of our books have a reasonably high minimum order size to avoid them getting cluttered up with tiny orders.

## Gas Top Up

If Allow Gas Top-Up is disabled (the default), and there are so many matching orders in the book that matching your Good Till Cancel order against them all is too expensive to do in one go, the remaining unfilled portion of the order will be cancelled after matching as many as possible. The order will not be added to the book if this happens.

If Allow Gas Top-Up is enabled, and there are so many matching orders in the book that matching your Good Till Cancel order against them all is too expensive to do in one go, your order will be moved to a special 'Needs Gas' status after matching as many as possible. You can then either cancel the remaining unmatched portion of the order, or 'Continue Placing' the order, adding more gas.

This mostly affects very large orders at a generous price - the exchange UI will warn you if your order looks like it may be expensive to match, and suggest enabling gas-top up.

## Fees

A fee of 0.2% of the matched amount is deducted from the amount the taker receives from each trade. For buy orders, the fee is in the base currency; for sell orders it is in the counter currency. The maker (provider of liquidity) pays no fees.

Example 1: The FOO/ETH Book has an offer to sell 10,000 FOO @ 1.50. You place an order to buy 2000 FOO @ 1.50, which costs you 3000 ETH. You are the taker on this trade, so you pay a fee of 4 FOO (0.2% of 2000) and receive the remaining 1996 FOO.

Example 2: You place an order to buy 200 FOO @ 1.50, which costs you 300 ETH. It is not matched and rests on the book. Another client places an order to sell 1000 FOO @ 1.50, of which 200 FOO (300 ETH) can be matched with you. They are the taker, so they pay a fee of 0.6 ETH (0.2% of 300), and receive the remaining 299.4 ETH. You receive the full 200 FOO.

Alternatively, and not yet available, AMIS Tokens (AMIS) can be used instead of ETH (at a fixed exchange rate) to pay AMIS Exchange fees on all markets that have ETH as a currency (base or counter).

Example 3: You prefer to pay fees using your AMIS tokens, so you deposit 200 AMIS into the FOO/ETH book contract to cover future fees. You then sell some FOO tokens for 100 ETH. Instead of 0.2 ETH being deducted from your 100 ETH, AMIS is deducted from your AMIS Exchange balance at 0.1% fee - **NOTE: This feature is not available yet.**

Fees paid by traders are held in the book contract on behalf of the contract creator.

## Gas limit per txs type summary

Table representing Gas limit usage per transaction type compared with the competition:

|**Action**|**AMIS Dex Fee**|**Amis Dex**|**Etherdelta**|**Ethen**|**Oasis**|**0x**|
|**Type**|Subject to change|**Gas used**|**Gas used**|**Gas used**|**Gas used**|**Gas used**|
|Deposit Eth|none|100,000|90000|44376|TBC|TBC|
|Deposit Token|none|200,000|82287|TBC|TBC|TBC|
|Withdraw Eth|none|100,000|22900|37489|TBC|TBC|
|Withdraw Token|none|100,000|48111|TBC|TBC|TBC|
|Place Order (Maker-Only)|none|300,000|TBC|TBC|TBC|TBC|
|Place Order (GTC / IoC)|0.2% of liquidity taken|300,000 + 100,000 for each order matched|93050-122986 per single order|135909-165581|108199-241277|TBC|
|Cancel Order|none|150,000|?|TBC|62090|TBC|

## Order Lifecycle

7 types of Order states defined:

|**ID #**|**Order State**|**Description**|
|1|Sending|- Your order is being sent via the Ethereum network to the exchange contract|
|2|Failed Send| - Your order could not be sent to the Ethereum network|
|3|Failed Txn| - Your order was sent to the Ethereum network but was not processed by the exchange contract|
|4|Rejected| - The exchange contract could not place your order (e.g. size too small)|
|5|Needs Gas| - See Gas Top Up section|
|6|Open| - Your order is resting on the book and waiting for others to fill it (or you to cancel it)|
|7|Done| - Your order has either been completely filled, or it has been cancelled. Nothing else can happen to it.|

In some cases, Orders such as Rejected and Done have a further Reason Code describing the root cause of that state, which can either be:

|**ID #**|**Reason Code**|**Description**|
|1|Invalid Price| - The price of the order was too low or too high|
|2|Invalid Size| - The size of the order (either in base or counter currency) was too small|
|3|Insufficient Funds| - Your exchange balance does not have enough funds to place this order|
|4|Would Take| - Your Maker Only order would immediately match another order|
|5|Unmatched| - Your Immediate or Cancel order was cancelled because it could not be matched|
|6|Too Many Matches| - The limit on matches prior to entering the book has been reached (see Gas Costs section)|
|7|Client Cancel| - You cancelled the order.|

## Confirmations, Forks, and Orphaned Transactions

AMIS Dex Orderbook and order matching engine run entirely on the Ethereum blockchain. The nature of the blockchain means that thousands of Ethereum nodes around the world are busy working to collectively agree on the state of the blockchain - in particular, to agree on which orders are in the order book, and on the state of each order.

Like all blockchains, sometimes this agreement (or consensus) isn't reached - groups of Ethereum nodes can temporarily disagree about which transactions (such as orders being placed) have been accepted into the blockchain. Normally, these disagreements are quickly resolved (in under a minute) and one group's view of the world wins, with transactions from the losing group being merged in where possible. (You might find the terms "Uncle Block" or "Chain Re-organization" useful if you want to read more).

Unfortunately, it is still possible (though rare) that a transaction can appear to have been accepted into the blockchain, but a short while later turn out to be rejected (that is, not confirmed).

If this occurs for an order-related transaction then clients may see odd behaviour in the AMIS Exchange Web UI such as:

 - depth appearing in the order book, only to disappear again;
 - ‎an open order appearing to be filled, only for it to return to an unmatched state;
 - ‎an apparently cancelled order returning to an open state.

We are working with the Ethereum development community to establish and apply best practices for how to shield clients from this uncertainty, or to convey it meaningfully. Unfortunately the approach taken by centralized exchanges to wait for a certain number of confirmations on deposit doesn't work on-chain - it's not just deposits that can be reverted.

For now, we recommend clients mitigate against this risk by waiting several Ethereum blocks (e.g. 12 blocks) before treating a trade or order state as final. This is particularly important for clients arbitraging between AMIS Exchange and off-chain exchanges.

Clients should be aware that pending transactions are visible to other Ethereum nodes, and that it is possible for Ethereum miners to re-order pending transactions.

## Smart contract release

From time to time, we may release a new smart exchange contract for a trading pair and make the AMIS Exchange web UI point to the new contract. For example, we might do this to improve performance, add features, or adjust minimum order sizes.

When this happens, orders from the old contract will not be copied to the new contract - the new book will start empty. We will try to provide several days notice before introducing a new contract, though exceptions may be made for security issues.

We aim to provide easy web UI access to each old contract for at least 3 months so orders / balances in the old contract can be cancelled, withdrawn or inspected. The contract itself is unstoppable - clients can continue to use the old contract via other interfaces.

## Marketplace Participants

The AMIS Dex exchange contract has no notion of sign-up, approval, or indeed KYC in its current state; however due to regulatory constraints we decided to develop a similar ecosystem which would enforce KYC/AML procedures. This new ecosystem is not ready yet, its conception relies on the current release which will evolve for the purpose of experimental code improvement and to better cope with legal and regulation requirements.

However, we ask that our beta tester(s) do :
- act honestly in dealings with other market participants;
- act fairly, dealing with other market participants in a consistent and appropriately transparent manner;
- act with integrity, avoiding questionable practices and behaviours;
- act cautiously, aware that some other market particpants may not follow these guidelines.

## Terms and Conditions

The AMIS Exchange Solidity Contracts, Web UI, and software libraries ("the Dapp") are provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement.

In no event shall the authors or copyright holders ("the software suppliers") be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the Dapp or the use or other dealings in the Dapp.

The Dapp should be considered its own autonomous entity as far as permitted by law - it is your responsiblity to study its likely behaviour before interacting with it, including taking into account that the actual behaviour of the compiled contract in a real Ethereum node may differ from the assumed behaviour based on the apparent intent of the Solidity source code, or differ from the trading rules in this page.

The Dapp contracts will live as long as the Ethereum blockchain, but no warranty is given that the AMIS Exchange website will continue to provide access to the contracts.

The software suppliers are unable to and will not cancel, undo, or make good any erroneous trades - all trades are final, even in the case of palpable errors made by market participants or the software suppliers themselves. The software suppliers are not responsible for the behaviour of other market participants.

The software suppliers do not in any way endorse the suitability of tokens offered for sale on the exchange. Nothing on this website should be taken as financial advice.

By interacting with the Dapp you agree to accept the conditions in this section as well as those listed at ethereum.org/agreement.
