---
layout:       post
title:        "Paper wallet 💵"
description:  "An approach for generating public and private keys for your crypto"
date:         2019-05-20 20:00:00 +0200
categories:   crypto
image:        /assets/img/post/paper-wallet-0.png
---

![Cover]({{ page.image }})

## Give me my money

Today's topis is something different. I heard that many people are investing in some stocks, jewelery collections or cryptocurrencies. When I looked closer at the last mentioned approach I noticed that people are buying some small amount of crypto and store them on crypto exchange. Exchange serivces work properly so there is no problem. But what happend when this crypto exchange will be closed one day? Or will you do when there is a maintenance break at particular moment when you need some of your coins?

## "If you don't own your private keys, you don't own the coins"

If you have something on a crypto exchange, it means that in the exchange's internal database particular value is assigned to your account (mostly your e-mail address). When you want to withdraw something you make a disposition to the crypto exchange and after a while they send proper value from their "real crypto account" and change the balance on your account. This is the reason why it is not so fast and a transaction fee of this operation is more expensive than typical transfering between crypto accounts (an exchange also takes some extra fee).

If something wrong happens like some "improvements" in the database, changes in the policy of the exchange or other stuff - it will be your problem. Anyone remembers [Mt.Gox](https://en.wikipedia.org/wiki/Mt._Gox)?

## Public key and private key

Most cryptocurrencies wallets contains two values: public key and private key. You can think about them using this analogy:
- public key - your account number
- private key - your password

The "key" is to share your public key among your friends and gather as many coins as you can on your account and do not share a private key with anoyone. 😉

## Paper wallet

To generater these pairs you can use a lot of stuff like a special application on your computer, an application on your mobile device, web wallets, hardware wallets etc. but I think that the fastest and easier way is to use paper wallet.

`Paper wallet` is just your public and private key written on the paper. There are many websites to generate them. You can print generated values, save them in your hidden and encrypted directory or even try to know by heart. 😉 It is a free of charge solution and everyone can do it right now.

## Generating a paper wallet

### The fastest way:

1. Search for the phrase `paper wallet generator [cryptocurrency]` (change `[cryptocurrency]` with your desired cryptocurrency like `Bitcoin`) on the web
2. Open the website
3. Check the opinions about this website
4. Generate a pair using this website and store it

### The "quite secure" steps are particular:

1. Search for the phrase `paper wallet generator [cryptocurrency]` (change `[cryptocurrency]` with your desired cryptocurrency like `Bitcoin`) on the web
2. Check the opinions about this website
3. Check if it contains github repository
4. Open this repository, read the whole code, understand it and download the codebase
5. Copy the codebase to the brand new computer which is off-line all the time
6. Open the downloaded codebase, generate a pair and store it

If you are not a "security freak", the "best effort approach" is in the middle (running the website locally on your computer).

The example of paper wallet for `Bitcoin` could be [bitaddress.org](https://www.bitaddress.org/). Open the website, move your mouse around to add some extra randomness or type some random characters into this textbox and see the results.

![Using bitaddress.org to generate paper wallet](/assets/img/post/paper-wallet-1.png)

## Better solutions

It could be easy to forget about the proper sequence of characters in your private key. Moreover you have only this one particular address for every transactions (although for many people it could be an advantage, "one to rule them all"). More flaws are listed on [en.bitcoin.it/wiki/Paper_wallet](https://en.bitcoin.it/wiki/Paper_wallet).

`Seed phrase` approach is recomendend right now and in the future I will try to write something about it.

If you would like you to trade coins stored on your paper wallet - yes, you need to transfer your coins to the crypto exchange back again. The solution is using decentralized crypto exchanges where you have your keys stored locally on your device, but they are not popular nowadays.

## Conclusions

- Try not to store a large ammount of your coins on crypto exchnages.
- Securely storing a private key by you makes sure that you are the owner of your coins.
- Start with generating paper wallets. Look for other solutions if this option is not suitable for you.
