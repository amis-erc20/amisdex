---
layout: page
title: Tutorial
subtitle: Depositing Tokens and Selling them using MetaMask
---

In this tutorial, we're going to deposit ERC20 Tokens into AMIS Exchange and sell them for Ether.

This version of the tutorial assumes you've installed and are using the [MetaMask Chrome Extension](https://metamask.io/), [Nifty Chrome Extension](https://chrome.google.com/webstore/detail/nifty-wallet/jbdaocneiiinmjbjlgalhcelgbejmnid) or [TrustWallet](https://play.google.com/store/apps/details?id=com.wallet.crypto.trustapp).

If you don't want to (or can't) use MetaMask, we have another [version for MyEtherWallet users](../depositing-tokens-and-selling-using-myetherwallet).

### Choosing MetaMask

First, make sure you've unlocked your MetaMask / Nifty / Trust Wallet account by entering your password and selected the address you want to use with AMIS Exchange.

The address will need enough tokens for your deposit, plus a little Ether (say 0.05 ETH) to cover gas fees.

Go to the pair you want to sell - in our case [AMIS-ETH](https://amis-erc20.github.io/amisdex/exchange/?pairId=AMIS-ETH) - and when asked "How should AMIS Exchange send Ethereum transactions?", choose MetaMask.

You might need to reload the AMIS Exchange web page after unlocking your MetaMask account - sometimes it doesn't detect it straight away.

### Depositing Tokens - Steps

Now AMIS Exchange knows to use your MetaMask  / Nifty / Trust Wallet account, you should see your Ethereum address balance appear as an "External" ETH balance in AMIS Exchange.

Your AMIS balance will also appear as an "External" AMIS balance. Your "Exchange" balance will likely be zero though.

In order to sell your AMIS on AMIS Exchange, you'll need to deposit them into the AMIS Exchange book contract. Note that each pair is a separate contract.

Use the "[+ Dep]" button next to your AMIS balance to bring up the Deposit AMIS form.

Depositing ERC20 tokens to a contract is a two-step process - first you have to "approve" the contract to use the tokens, then the contract has to "collect" them.

(Warning: Never transfer tokens directly to a contract - the contract won't know whose they are and they will be lost forever).

### Depositing Tokens - Approve

Step 1 of the Deposit AMIS form shows the "current approved amount" as zero. We're going to deposit 100000 AMIS, so we need to enter 100000 in the new approved amount and click Approve.

When you click 'Approve', MetaMask will pop-up its "Confirm Transaction" dialog - check the details look sensible and click Confirm.

Tips:
 - You'll need some Ether in your metamask account for paying gas fees;
 - When the Ethereum network is busy, transactions can take a while - increasing the "gas price" on the Confirm Transaction dialog can help (at the cost of paying a higher fee);

After the transaction has completed, you should see the "current approved amount" change to 100000. However, we still can't use it - onto the next step.

### Depositing Tokens - Collect

Now that you've approved the exchange to receive 100000 of your AMIS tokens, click "Collect" in Step 2 of the Deposit AMIS form to tell the exchange contract to actually receive them.

When you click 'Collect', MetaMask will pop-up its "Confirm Transaction" dialog - check the details look sensible and click Confirm.

This time once the transaction has completed, we can see back up in the balance section that our "Exchange" AMIS balance is now 100000. We're ready to sell our tokens.

### Selling Tokens

Now we have an "Exchange" AMIS balance, we're going to offer to sell our tokens.

Let's pretend we're not happy with the best bid offered in the order book - we're going to set our own price and hope someone fills our order later.

We'll make sure 'SELL AMIS' is selected, enter the number of tokens we want to sell in the amount box, and enter the price we're hoping for in the price box.

The default "Good Till Cancel" terms would be ok, but for this tutorial since we're offering a price (rather than taking someone else's) we're going to choose "Maker Only" terms.

Choosing "Maker Only" means that our order will be cancelled if it would immediately get matched (as might happen if our price turned out to be too generous). It's also a bit cheaper in terms of gas. Full details of terms and order statuses are covered in our [Trading Rules guidelines](../../trading-rules).

When we click 'Place Sell Order', MetaMask will pop-up its "Confirm Transaction" screen - check the details look sensible and click Confirm.

You can check the progress of the transaction in MetaMask.

![](https://raw.githubusercontent.com/amis-erc20/amisdex/master/help/deposit-and-sell-tokens-with-metamask.gif)

Eventually, we should see:
 - our AMIS balance go down to 0 since they're all tied up in our open order;
 - our sell order appear as an open order is the "My Orders" section;
 - our order appear in the Ask side of the orderbook.

Sometimes difficulties communicating with the Etherum Network can cause updates to get lost - you may need to hit reload after waiting a few minutes.

If we change our minds and decide we don't want to offer this price any more, we can cancel our order via the My Orders section.

Congratulations - you're an unstoppable trader now!
