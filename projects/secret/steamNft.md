---
tags: crypto secret steam rust js react working_on
---
# nft to steamitem lottery.
```
tldr: skins are sent to admin server where it get proccsesd and value checked. Later funds are added to contract that lets sender gamble and go into pool where median is the buying price.
```

- [nft to steamitem lottery.](#nft-to-steamitem-lottery)
- [big todo](#big-todo)
  - [loot_back](#loot_back)
  - [contract](#contract)
  - [0.1. scuffed pitch](#01-scuffed-pitch)
- [1. nft gamble/mint](#1-nft-gamblemint)
- [2. withdraw](#2-withdraw)
- [3. deposit](#3-deposit)
- [4. lootcontract](#4-lootcontract)
- [5. frontend](#5-frontend)

# big todo
## loot_back
> X setup steam and pass it to components
> X setup secretjs and pass it to components
    X add envitomental variables

> withdraw
    x pool for code every 3 min for added burn
    x    pool compare contract arr and current arr and filter awawy already sent steamids
    verify it works with steam
    x get tokenid from json and use it for withdraw

> deposit
    x check that it calls correct to contract
    x check with steam
## contract
> update test with new tokenid system
> change name and ids to make more sense
> dont calculat buyin when theres 1 item left

## 0.1. scuffed pitch
    on site token -> buy in on gamble token to nft contract. nft sent to winners wallet
# 1. nft gamble/mint

# 2. withdraw
    contract revice nft and adds to burn nft list. if got steamid send out tradeoffer with item.
# 3. deposit
    listens for trade. get item and tradelink from trademsg. minter send to contract and add funds to adress sent in msg.
# 4. lootcontract
    deposit for funds
    use funds to roll
    nft is minted 
    send nft to contract
    skin is sent.

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
        TODO 1 items left bugg
        DONE stop from going negativ
    quary()
        DONE getPoolData
        DONE getFunds(account)

# 5. frontend
```
if need to improve loot box
https://react-spring.io/hooks/use-transition#usetransition
https://medium.com/@victortoschi/how-to-create-a-slot-machine-animation-with-css-and-javascript-9073ab9db9ea
```    

link to community market [fetch](https://steamcommunity.com/market/priceoverview/?appid=730&currency=1&market_hash_name=%27Two%20Times%27%20McCoy%20|%20USAF%20TACP) 
image fetch https://api.steamapis.com/image/item/730/%27Two%20Times%27%20McCoy%20|%20USAF%20TACP
animation creat list of random items. css animaion to allways land on x box in the list
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