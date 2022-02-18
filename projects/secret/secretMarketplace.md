---
tags: crypto secret rust js react todo
---
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

## table for listings
## table for categories/tags