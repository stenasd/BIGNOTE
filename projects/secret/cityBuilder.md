---
tags: crypto secret gamedev rust js react
---

# towngame
- init city cost set crypto ex 20kr.
- villagers = nft got expireblock and stats that affect new nft villgers and town actions. private exact time it dies. date born and health stat to guees lifespan is public.
- town stats affect stats of new nfts(villagers)
- town dies if no villagers left and contract stop accepting calls

# town loop
- util upkeep cost that villg maintain
- wealth incease migrant stats
- admin increase migrant quality
- quality freq of action town can take
- actions. creat upkeep. accept migrant

# villager
- stats that increase wealth/admin/quality

# if time
- food and other currency to keep town alive
- nfts generate exp to build stuff
- buildings to modify nfts more ex: hospital increase age of nft

# psudo
        setowner
        start town.
        generate villagers to buyer
        setstorage with time to keep track of cooldown
        handle functions to withdraw nfc, approve villager, upgrade town,

- store town data and next avalilable action
- calcStatsFromVillg
- getVillg
- remove villg
- add villg

        villg{
            stat1:0,
            stat2:0,
            stat3:0,
            name:"",
        }
        city[
            {
                owner:""
                name:""
                pop:[villg]
                stat1:0,
                stat2:0,
                stat3:0
            }
        ]
# contract todo

- get metadata and store in contract
- create town
- store nft in town
