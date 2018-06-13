---
layout: page
title: Tutorial
subtitle: Depositing Ether and Buying Tokens using MyEtherWallet
---

In this tutorial, we're going to deposit Ether into KIWI Exchange and use it to buy OMG tokens.

This version of the tutorial assumes you have a wallet on [MyEtherWallet.com](https://www.myetherwallet.com/) you want to use.

If you don't want to use MyEtherWallet, we have another [version for MetaMask users](../depositing-ether-and-buying-tokens-using-metamask).

### Choosing MyEtherWallet

First, make sure you've unlocked your MyEtherWallet wallet on the [MyEtherWallet Send Ether & Tokens](https://www.myetherwallet.com/#send-transaction) page and know which address you will use with KIWI Exchange.

The address will need enough Ether for your deposit, plus a little extra (say 0.05 ETH) to cover gas fees.

Go to the pair you want to buy - in our case [OMG-ETH](http://exchange.thekiwi.io/exchange/?pairId=OMG-ETH) - and when asked "How should KIWI Exchange send Ethereum transactions?", choose "Tell me what to send via MyEtherWallet" and copy-and-paste your MyEtherWallet Account Address.

Here's a little video showing what to do:

![Connecting with MyEtherWallet Video](../connect-with-mew.gif)

### Depositing Ether

Now KIWI Exchange knows to use your MyEtherWallet account, you should see your Ethereum address balance appear as an "External" ETH balance in KIWI Exchange.

In order to use your Ether to buy tokens, you'll need to deposit it into the KIWI Exchange book contract. Note that each pair is a separate contract.

Use the "[+ Dep]" button next to your ETH balance to bring up the Deposit ETH form.

When you click the "Deposit Eth" button, KIWI Exchange will not send anything - instead it will tell you what to send.

You'll need to copy-and-paste the details (address, amount, gas and data) into MyEtherWallet, then generate and send the transaction in MyEtherWallet.

Make sure to include the "Data" - you might need to click "+ Advanced: Add Data" in MyEtherWallet.

Here's a video:

![Depositing Ether with MyEtherWallet Video](../deposit-ether-with-mew.gif)

Tips:
 - Make sure you leave some Ether in your account since you'll need it to pay gas fees;
 - You can check the progress of your transaction using the "Transaction History" in MyEtherWallet;
 - MyEtherWallet might show a error while you're filling in the form - this will go away once the gas and data are complete.

After the transaction has completed, you should see your "Exchange" ETH balance on KIWI Exchange increase (and your "External" balance decrease).

### Buying Tokens

Now we have an "Exchange" ETH balance, we're going to use it to buy 4 OMG tokens, taking the price of 0.0330 we can see offered in the "Ask" side of the book.

We'll make sure 'Buy OMG' is selected, enter the number of tokens we want to buy in the amount box, fill in the price box by clicking the price we want, then choose the default terms of "Good Till Cancel (no gas topup)".

"Good Till Cancel" means that even if the offer we saw disappears, our order to buy will still stand - it will be added to the book and (hopefully) filled by someone else. If we don't want that, we could choose "Immediate or Cancel". Full details of terms and order statuses are covered in our [Trading Rules](../../trading-rules).

When you click 'Place Buy Order', KIWI Exchange will will not send anything - instead it will tell you what to send.

You'll need to copy-and-paste the details (address, amount, gas and data) into MyEtherWallet, then generate and send the transaction in MyEtherWallet.

Here comes the video:

![TODO - Buy Tokens with MyEtherWallet Video](../buy-tokens-with-mew.gif)

Finally, you should have 0.3998 OMG in your "Exchange" OMG balance (after the teeny 0.0002 OMG fee). Click "[- Wtd]" button to withdraw to your MyEtherWallet account.

Congratulations - you're an unstoppable trader now!
