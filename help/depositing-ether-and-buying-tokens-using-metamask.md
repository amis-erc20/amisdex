---
layout: page
title: Tutorial
subtitle: Depositing Ether and Buying Tokens using MetaMask / Nifty / TrustWallet
---

In this tutorial, we're going to deposit Ether into AMIS Exchange and use it to buy AMIS tokens.

This version of the tutorial assumes you've installed and are using the [MetaMask Chrome Extension](https://metamask.io/), [Nifty Chrome Extension](https://chrome.google.com/webstore/detail/nifty-wallet/jbdaocneiiinmjbjlgalhcelgbejmnid) or [TrustWallet](https://play.google.com/store/apps/details?id=com.wallet.crypto.trustapp).

If you don't want to (or can't) use MetaMask/Nifty/TrustWallet, we have another [version for MyEtherWallet users](../depositing-ether-and-buying-tokens-using-myetherwallet).

### Choosing MetaMask

First, make sure you've unlocked your MetaMask account by entering your password and selected the address you want to use with AMIS Exchange.

The address will need enough Ether for your deposit, plus a little extra (say 0.05 ETH) to cover gas fees.

Go to the pair you want to buy - in our case [AMIS-ETH](http://amis-erc20.github.io/amisdex/exchange/?pairId=AMIS-ETH) - and when asked "How should AMIS Exchange send Ethereum transactions?", choose MetaMask.

You might need to reload the AMIS Exchange web page after unlocking your MetaMask account - sometimes it doesn't detect it straight away.

### Depositing Ether

Now AMIS Exchange knows to use your MetaMask account, you should see your Ethereum address balance appear as an "External" ETH balance in AMIS Exchange.

In order to use your Ether to buy tokens, you'll need to deposit it into the AMIS Exchange book contract. Note that each pair is a separate contract.

Use the "[+ Dep]" button next to your ETH balance to bring up the Deposit ETH form.

When you click 'Deposit ETH', MetaMask will pop-up its "Confirm Transaction" dialog - check the details look sensible and click Confirm.

Tips:
 - Make sure you leave some Ether in your account since you'll need it to pay gas fees;
 - When the Ethereum network is busy, transactions can take a while - increasing the "gas price" on the Confirm Transaction dialog can help (at the cost of paying a higher fee);
 
 ![](https://raw.githubusercontent.com/amis-erc20/amisdex/master/help/deposit-with-metamask.gif)

After the transaction has completed, you should see your "Exchange" ETH balance on AMIS Exchange increase (and your "External" balance decrease).

### Buying Tokens

Now we have an "Exchange" ETH balance, we're going to use it to buy 100000 AMIS tokens.

We'll make sure 'Buy AMIS' is selected, enter the number of tokens we want to buy in the amount box, fill in the price box by clicking the price we want, then choose the default terms of "Good Till Cancel (no gas topup)".

"Good Till Cancel" means that even if the offer we saw disappears, our order to buy will still stand - it will be added to the book and (hopefully) filled by someone else. If we don't want that, we could choose "Immediate or Cancel". Full details of terms and order statuses are covered in our [Trading Rules](../../trading-rules).

When we click 'Place Buy Order', MetaMask will pop-up its "Confirm Transaction" screen - check the details look sensible and click Confirm.

![](https://raw.githubusercontent.com/amis-erc20/amisdex/master/help/buy-tokens-with-metamask.gif)

Finally, you should have 9800 AMIS in your "Exchange" AMIS balance (after the teeny (0.2%) 200 AMIS fee). Click "[- Wtd]" button to withdraw to your MetaMask account.

Congratulations - you're an unstoppable trader now!
