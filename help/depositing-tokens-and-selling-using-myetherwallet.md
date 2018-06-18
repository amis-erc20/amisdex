---
layout: page
title: Tutorial
subtitle: Depositing Tokens and Selling them using MyEtherWallet
---

In this tutorial, we're going to deposit ERC20 Tokens into KIWI Exchange and sell them for Ether.

This version of the tutorial assumes you have a wallet on [MyEtherWallet.com](https://www.myetherwallet.com/) you want to use.

If you don't want to use MyEtherWallet, we have another [version for MetaMask users](../depositing-tokens-and-selling-using-metamask).

### Choosing MyEtherWallet

First, make sure you've unlocked your MyEtherWallet wallet on the [MyEtherWallet Send Ether & Tokens](https://www.myetherwallet.com/#send-transaction) page and know which address you will use with KIWI Exchange.

The address will need enough enough tokens for your deposit, plus a little Ether (say 0.05 ETH) to cover gas fees.

Go to the pair you want to buy - in our case [KIWI-ETH](http://exchange.thekiwi.io/exchange/?pairId=KIWI-ETH) - and when asked "How should KIWI Exchange send Ethereum transactions?", choose "Tell me what to send via MyEtherWallet" and copy-and-paste your MyEtherWallet Account Address.

### Depositing Tokens - Steps

Now KIWI Exchange knows to use your MyEtherWallet account, you should see your Ethereum address balance appear as an "External" ETH balance in KIWI Exchange.

Your KIWI balance will also appear as an "External" KIWI balance. Your "Exchange" balance will likely be zero though.

In order to sell your KIWI on KIWI Exchange, you'll need to deposit them into the KIWI Exchange book contract. Note that each pair is a separate contract.

Use the "[+ Dep]" button next to your KIWI balance to bring up the Deposit KIWI form.

Depositing ERC20 tokens to a contract is a two-step process - first you have to "approve" the contract to use the tokens, then the contract has to "collect" them.

(Warning: Never transfer tokens directly to a contract - the contract won't know whose they are and they will be lost forever).

### Depositing Tokens - Approve

Step 1 of the Deposit KIWI form shows the "current approved amount" as zero. We're going to deposit 100000 KIWI, so we need to enter 10 in the new approved amount and click Approve.

When you click 'Approve', KIWI Exchange will tell you what transaction you need to make via MyEtherWallet's "Send Ether and Tokens" page.

For security, KIWI Exchange won't make transactions for you - you'll need to go to copy-and-paste the details (address, amount, gas and data) into MyEtherWallet, then generate and send the transaction in MyEtherWallet.

Make sure to include the "Data" - you might need to click "+ Advanced: Add Data" in MyEtherWallet.

Tips:
 - You'll need some Ether (not just tokens) in your MyEtherWallet account for paying gas fees;
 - You can check the progress of your transaction using the "Transaction History" in MyEtherWallet;
 - MyEtherWallet might show a error while you're filling in the form - this will go away once the gas and data are complete.

After the transaction has completed, you should see the "current approved amount" change to 10. However, we still can't use it - onto the next step.

### Depositing Tokens - Collect

Now that you've approved the exchange to receive 10 of your KIWI tokens, click "Collect" in Step 2 of the Deposit KIWI form to tell the exchange contract to actually receive them.

As before, KIWI Exchange will tell you what transaction you need to make via MyEtherWallet's "Send Ether and Tokens" page - you'll need to copy-and-paste the details  (address, amount, gas and data) into MyEtherWallet, then hit Generate and Send Transaction.

This time once the transaction has completed, we can see back up in the balance section that our "Exchange" KIWI balance is now 100000. We're ready to sell our tokens.

### Selling Tokens

Now we have an "Exchange" KIWI balance, we're going to offer to sell our tokens.

Let's pretend we're not happy with the best bid offered in the order book - we're going to set our own price and hope someone fills our order later.

We'll make sure 'SELL KIWI' is selected, enter the number of tokens we want to sell in the amount box, and enter the price we're hoping for in the price box.

The default "Good Till Cancel" terms would be ok, but for this tutorial since we're offering a price (rather than taking someone else's) we're going to choose "Maker Only" terms.

Choosing "Maker Only" means that our order will be cancelled if it would immediately get matched (as might happen if our price turned out to be too generous). It's also a bit cheaper in terms of gas. Full details of terms and order statuses are covered in our [Trading Rules](../../trading-rules).

When we click 'Place Sell Order', KIWI Exchange will tell you what transaction you need to make via MyEtherWallet's "Send Ether and Tokens" page - you'll need to copy-and-paste the details (address, amount, gas and data) into MyEtherWallet, then hit Generate and Send Transaction.

Eventually, after the transaction is complete, we should see:
 - our KIWI balance go down to 0 since they're all tied up in our open order;
 - our sell order appear as an open order is the "My Orders" section;
 - our order appear in the Ask side of the order book.

Sometimes difficulties communicating with the Etherum Network can cause updates to get lost - you may need to hit reload after waiting a few minutes.

If we change our minds and decide we don't want to offer this price any more, we can cancel our order via the My Orders section.

Congratulations - you're an unstoppable trader now!
