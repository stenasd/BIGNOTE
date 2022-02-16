---
tags: crypto secret
---

# linux commands

- upload
    ```
    secretcli tx compute store nftcontr.wasm --from a --gas 10000000 -y --keyring-backend test
    secretcli tx compute store contract.wasm.gz --from a --gas 1000000 -y --keyring-backend test
    secretcli query compute list-code
    ```

- init
        
                INIT='{"count": 100000000}'
                CODE_ID=2
                secretcli tx compute instantiate $CODE_ID "$INIT" --from a --label "my counter" -y --keyring-backend test

- init coin
    ```
    INIT='{"name": "villagers","symbol": "vilg"}'
    CODE_ID=1
    secretcli tx compute instantiate $CODE_ID "$INIT" --from a --label "my nft" -y --keyring-backend test
    ```

- With the contract now initialized, we can find its address

        secretcli query compute list-contract-by-code 1

- query

        CONTRACT=secret10pyejy66429refv3g35g2t7am0was7ya6hvrzf
        secretcli query compute query $CONTRACT  '{"get_settings": {}}'

- execute
    ```
    CONTRACT=secret1fap6ujln7l2l24yrlzuq2am6nakdgvcmlrhu6x
    secretcli tx compute execute $CONTRACT '{"increment": {}}' --from a --keyring-backend test
    secretcli tx compute execute $CONTRACT '{"reset": {}}' --from a --keyring-backend test

    {
    "code_id": 1,
    "creator": "secret1rmet6t5x9kzzdst77xrqn4csfk29lm220nc7sf",
    "label": "my counter",
    "address": "secret18vd8fpwxzck93qlwghaj6arh4p7c5n8978vsyg"
    }
    ```
- docker

        docker run -it --rm  -p 26657:26657 -p 26656:26656 -p 1337:1337  -v $(pwd):/root/code  --name secretdev enigmampc/secret-network-sw-dev

        docker exec -it secretdev /bin/bash

        secretcli keys list --keyring-backend test
- compile 
    ```
    $ rustup target add wasm32-unknown-unknown
    $ sudo apt install binaryen
    $ RUSTFLAGS='-C link-arg=-s' cargo build --release --target wasm32-unknown-unknown --locked
    $ wasm-opt -Oz ./target/wasm32-unknown-unknown/release/*.wasm -o ./contract.wasm
    $ cat ./contract.wasm | gzip -9 > ./contract.wasm.gz
    ```

- mint 
    ```
    secretcli tx compute execute secret18vd8fpwxzck93qlwghaj6arh4p7c5n8978vsyg '{
            "mint_nft": {
                    "token_id": "optional_ID_of_new_token",
                    "owner": "optional_address_the_new_token_will_be_minted_to",
                    "public_metadata": {
                            "token_uri": "optional_uri_pointing_to_off-chain_JSON_metadata",
                            "extension": {
                                    "image": "https://preview.redd.it/sieamg5syj181.png?width=640&crop=smart&auto=webp&s=95f46bc80b290f696687b302b52ad9632f658191",
                                    "description": {
                                            "stat1": 1,
                                            "stat2": 2,
                                            "stat3": 3
                                    },
                                    "name": "secret1245ejgnmskvmy4d5guwwc39u28uv644hqjmp64"
                            }
                    }
            }
    }' --from a --keyring-backend test
    ```

- clicommands
    ```
    secretcli tx send secret1vxzkyqvc97489c5axxcm0csgs95a6ctzjkl0r2 secret1saw872anvey9r2hrvyma8k89jh0cas0d44fkxp 10000000000uscrt
    secretcli q account secret1saw872anvey9r2hrvyma8k89jh0cas0d44fkxp

    secretcli q account secret1vxzkyqvc97489c5axxcm0csgs95a6ctzjkl0r2

    secretcli query compute list-code
    secretcli query compute list-contract-by-code 1


    CONTRACT=secret1xzlgeyuuyqje79ma6vllregprkmgwgavk8y798
    secretcli tx compute execute $CONTRACT '{"start_loot_pool": {}}' --from a --keyring-backend test
    client.execute(contract, msg, undefined, undefined, *fee*)
    ```