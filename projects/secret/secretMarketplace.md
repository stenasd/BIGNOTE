---
tags: crypto secret rust js react todo
---
## pitch: Escrow marketplace that is more secure, safe and quicker then tor alternatives using secret contracts. Live on clearnet and easily used by less tech savy. Like wickr for marketplaces



# anon crypto marketplace with mmr for sellers
```
tldr anon marketplace where the data and funds will never go away when the sites get busted or destroyed. Uses ranking for how trustworthy
```
# handle not getting scammed
Mmr system that give more used and older accounts higer impact on review. Have clear stats and reporting available for what went wrong. Example. disputed but payed back +rep, disputed but not payed back -rep . recived item +rep. 20% of buye price is on hold until buyer review.

# storage design

## table for users
humanAddr(): adress
> addres/auth to interact with contract

acceptedDispute: i32
> when buyer creat dispute and the seller rejects it

rejectedDispute: i32
> same but when rejected

createdDispute: i32
> when as buyer dispute is created

buyWithNoReview: i32
> when buyer dont leave review and lose buyin stake.

goodCommunicationUpvote:i32
> buyer can upvate when seller is good responding

Deliverd:i32
> buyer upvote if item was Deliverd

orderstuff
>succesfull orders,failed orders,

## table for listings
## table for categories/tags

# frontend
    node gui desktop and tor website.
    wallet with mnemonics saved local only.
    homepage is list with saved contract addresses and right hash.
# backend
    Query endpoint for data like seller listings and stats.
    init:
        tag,name
    handle:
        buy/create/cancel/dispute/send msg
    


