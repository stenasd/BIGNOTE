---
tags: crypto secret steam rust js react working_on
---
# nft to steamitem lottery.
```
tldr: skins are sent to admin server where it get proccsesd and value checked. Later funds are added to contract that lets sender gamble and go into pool where median is the buying price.
```

- [nft to steamitem lottery.](#nft-to-steamitem-lottery)
  - [0.1. scuffed pitch](#01-scuffed-pitch)
- [1. nft gamble/mint](#1-nft-gamblemint)
- [2. cashout](#2-cashout)
- [3. nftfunc](#3-nftfunc)
- [4. lootcontract](#4-lootcontract)
- [5. frontend](#5-frontend)
- [6. backend](#6-backend)
  
## 0.1. scuffed pitch
    on site token -> buy in on gamble token to nft contract. nft sent to winners wallet
# 1. nft gamble/mint

    buy in to randomize and transfer ownership of 2 nfts from owned nfts

    end user - trade in skins get currency

    currency buy nfts 

    nfts trade out for skin

    server->mint skins and give currency
    server-> give and take currency
    server-> currency to enter gamble contract with nfts as prize
    contract -> entry with currency and wallet adress. winning wallet gets nfts

    contract structs:
        nft metadata: skin price at mint. wear name, and when tradeable
        player data: walletadress and current currenciy
        rngpool: array with nfts in pool

    contract logic: buyin price = avarage price of skins

    handle: enter pool rng, minter reduce currency, minter increase currency, minter add to pool.

# 2. cashout

    trade in nft for skin = send to nft burn
    trade in for currency = send back to gamble contract and add currency

# 3. nftfunc

    getmetadata
    send/transfer ownership
    burn nft

# 4. lootcontract

    init()
        DONE nft adress and codehash
        DONE admin adress
        DONE recive nft
    handle()
        DONE recive nft and add to pool
        DONE caluclate pool worth
        DONE use funds to randomize skin
        DONE use adress as prefix
        DONE addFunds()
        DONE removeFunds()
    quary()
        getPoolData
        getFunds(account)

# 5. frontend
DONE upload nft and init it to testnet
DONE upload contract and init itvh
DONE get owned tokens in index
TODO Query contract info 
TODO Query contract pool and price
TODO sendNft To contract
```
main page
    on mobile combine to 1 panel and have tabs
    panel 3:
        buy in price and skins in pool.
    panel 2:
        owned nfts and click on nft to trade in/send to adress/
        logedin and login
        display owned nfts
    panel 1:
        gamble tokens
        show odds and stats ex fees and traffic
item page
    item info"nft_dossier" and option to link specific item
    specific steam inventory that owns it
    
click start roll a loading symbol starts and then when results come in show item won
```

# 6. backend

>  handle all add/remove funds to contract account. give out skin when turned in
> steamtrade
> log website action
> store and cashe in redis

> mysql that store steam traded items
