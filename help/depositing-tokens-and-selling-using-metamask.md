---
layout: page
title: Tutorial
subtitle: Depositing Tokens and Selling them using MetaMask
---

In this tutorial, we're going to deposit ERC20 Tokens into KIWI Exchange and sell them for Ether.

This version of the tutorial assumes you've installed and are using the [MetaMask Chrome Extension](https://metamask.io/).

If you don't want to (or can't) use MetaMask, we have another [version for MyEtherWallet users](../depositing-tokens-and-selling-using-myetherwallet).

### Choosing MetaMask

First, make sure you've unlocked your MetaMask account by entering your password and selected the address you want to use with KIWI Exchange.

The address will need enough tokens for your deposit, plus a little Ether (say 0.05 ETH) to cover gas fees.

Go to the pair you want to sell - in our case [KIWI-ETH](http://exchange.thekiwi.io/exchange/?pairId=KIWI-ETH) - and when asked "How should KIWI Exchange send Ethereum transactions?", choose MetaMask.

You might need to reload the KIWI Exchange web page after unlocking your MetaMask account - sometimes it doesn't detect it straight away.

### Depositing Tokens - Steps

Now KIWI Exchange knows to use your MetaMask account, you should see your Ethereum address balance appear as an "External" ETH balance in KIWI Exchange.

Your KIWI balance will also appear as an "External" KIWI balance. Your "Exchange" balance will likely be zero though.

In order to sell your KIWI on KIWI Exchange, you'll need to deposit them into the KIWI Exchange book contract. Note that each pair is a separate contract.

Use the "[+ Dep]" button next to your KIWI balance to bring up the Deposit KIWI form.

Depositing ERC20 tokens to a contract is a two-step process - first you have to "approve" the contract to use the tokens, then the contract has to "collect" them.

(Warning: Never transfer tokens directly to a contract - the contract won't know whose they are and they will be lost forever).

### Depositing Tokens - Approve

Step 1 of the Deposit KIWI form shows the "current approved amount" as zero. We're going to deposit 100000 KIWI, so we need to enter 100000 in the new approved amount and click Approve.

When you click 'Approve', MetaMask will pop-up its "Confirm Transaction" dialog - check the details look sensible and click Confirm.

Tips:
 - You'll need some Ether in your metamask account for paying gas fees;
 - When the Ethereum network is busy, transactions can take a while - increasing the "gas price" on the Confirm Transaction dialog can help (at the cost of paying a higher fee);

After the transaction has completed, you should see the "current approved amount" change to 100000. However, we still can't use it - onto the next step.

### Depositing Tokens - Collect

Now that you've approved the exchange to receive 100000 of your KIWI tokens, click "Collect" in Step 2 of the Deposit KIWI form to tell the exchange contract to actually receive them.

When you click 'Collect', MetaMask will pop-up its "Confirm Transaction" dialog - check the details look sensible and click Confirm.

This time once the transaction has completed, we can see back up in the balance section that our "Exchange" KIWI balance is now 100000. We're ready to sell our tokens.

### Selling Tokens

Now we have an "Exchange" KIWI balance, we're going to offer to sell our tokens.

Let's pretend we're not happy with the best bid offered in the order book - we're going to set our own price and hope someone fills our order later.

We'll make sure 'SELL KIWI' is selected, enter the number of tokens we want to sell in the amount box, and enter the price we're hoping for in the price box.

The default "Good Till Cancel" terms would be ok, but for this tutorial since we're offering a price (rather than taking someone else's) we're going to choose "Maker Only" terms.

Choosing "Maker Only" means that our order will be cancelled if it would immediately get matched (as might happen if our price turned out to be too generous). It's also a bit cheaper in terms of gas. Full details of terms and order statuses are covered in our [Trading Rules](../../trading-rules).

When we click 'Place Sell Order', MetaMask will pop-up its "Confirm Transaction" screen - check the details look sensible and click Confirm.

You can check the progress of the transaction in MetaMask.

Eventually, we should see:
 - our KIWI balance go down to 0 since they're all tied up in our open order;
 - our sell order appear as an open order is the "My Orders" section;
 - our order appear in the Ask side of the order book.

Sometimes difficulties communicating with the Etherum Network can cause updates to get lost - you may need to hit reload after waiting a few minutes.

If we change our minds and decide we don't want to offer this price any more, we can cancel our order via the My Orders section.

Congratulations - you're an unstoppable trader now!
