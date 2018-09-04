---
layout: post
title: Amis Dex On-chain Order Book live
subtitle: Amis Dex Experimental Developments in beta testing
tags: [dapp-developers]
---

At AMIS Exchange, we want to make it as easy as possible for new AMIS subscribers to start lending, borrowing, trading, transferring without compromising on security end to end. The Amis Dex On-chain Order Book solves the problem faced by most decentralized exchanges nowadays: centralized Order Book. On the contrary Amis Dex takes the opposite approach leveraging the power of decentralization by transparently publishing the orders on the chain. With this principle in mind, on can admit that On chain orders are not exposed nor subject to the attack surface and attack vectors affecting 0x relays, Idex & etherdelta/forkdelta centralized orderbooks and their associated APIs.

Being totally decentralized and in beta testing, AMIS Exchange doesn't have any sign-up or verification (KYC/AML) at the moment, so ideally new comers should be able to turn up, deposit and buy in minutes.

Orderbooks are critically important in a decentralized exchange ecosystem, with this in mind the Amis team developed on top of existing open source projects the Amis Dex decentralized app ("DApp") currently known as AMIS Exchange. The exchange is available on a 24/365 basis; we offer you to learn and practice on our demo or on testnet before going live on mainnet. Once trained one  can safely let the DApp send Ethereum transactions from their Ethereum address, in our case to buy and sell AMIS tokens on the exchange.

Amis Dex runs on any browser supporting MetaMask's extension, and DApps could just rely on that, but in practice there's at least five different ways clients want to send transactions:

 1. Manual Transactions (user copy-and-pastes details into e.g. MEW)
 2. Browser Extension (MetaMask)
 3. Dapp Browser / Local Client (Infura, Mist, Parity, Geth)
 4. Hardware Wallet (Ledger, Trezor)
 5. Imported Private Key / Keystore JSON / Mnemonic

Right now, AMIS Dex Exchange supports the first three - but we'll soon add improved security with hardware wallets integration plus a wide range of exciting cutting edge products ready to operate on any OS, from the pal of your hand right to any mobile device type capable of securely storing your imported private keys.

Foreseen developements around Javascript library that DApp dev could drop in to provide added functionalities like:

 - Create addresses, view balances
 - Select network + address to use
 - Confirm transactions, choose gas price
 - Sign messages
 - Transfer ETH + tokens between addresses
 - Show recent transaction history

And of course, for MetaMask clients the magical library would let MetaMask handle most of the above, and for Hardware Wallet clients it would talk to the hardware, and for private key clients it would provide its own User Interface for transactions and key management.

Naturally, the User Interface would be reskinnable to match the style of the Dapp using it, and all text displayed to clients would be internationalized with high quality translations into many languages.

Unfortunately, unless we're missing something, there's no library that quite does all the above out of the box - though there's lots of great lower-level building blocks, and some promising stuff out there. Here's a round up of libraries we've looked at:

[web3.js](https://github.com/ethereum/web3.js) - (Starting with the obvious one for completeness!) This is the core interface between JS and the Ethereum blockchain for most DApps. Quite low-level, currently undergoing a transition from 0.9 to 1.0.

[MetaMask/Mascara](https://github.com/MetaMask/mascara) - This does actually sound very much like the wished for magical library; a MetaMask user experience without needing to install MetaMask. Sadly not production ready yet, and no hardware wallet support.

[ethereumjs-wallet](https://github.com/ethereumjs/ethereumjs-wallet) - Lower-level library to generate private keys and decrypt/encrypt into various key store formats.

[web3 provider-engine](https://github.com/MetaMask/provider-engine) - The concept of "web3 provider engines" allows extra functionality to be added to the base web3.js - for example, by [ledger-wallet-provider](https://github.com/Neufund/ledger-wallet-provider), which provides support (but no UI) for connecting to the Ledger hardware wallet.

[ethjs-provider-signer](https://github.com/ethjs/ethjs-provider-signer) and [ethjs-signer](https://github.com/ethjs/ethjs-signer) - Minimal library that can add support to web3 for signing transactions with a private key.

[MyEtherWallet Source](https://github.com/kvhnuke/etherwallet/tree/mercury/app/scripts/staticJS) - Not a library as such, but the splendid folks at MyEtherWallet make their code available under a permissive license which allows us to take a little peek at how they do a great job of handling lots of wallet types ...

[ethers.js](https://github.com/ethers-io/ethers.js) - Similar to web3.js, has more wallet management built in and a nicer API. Part of the [ethers.io](https://docs.ethers.io/ethers-app/html/) system to make building DApps easier.
[0x project](https://github.com/0xproject) 0x project
[Dharma ralayer kit](https://github.com/dharmaprotocol/relayer-kit) Dharma protocol kit for relayers

