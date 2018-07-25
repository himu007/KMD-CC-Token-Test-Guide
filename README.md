# KMD-CC-Token-Test-Guide
Komodo CC Token testing description, setup &amp; how-to

## Table of Contents
[What is CC Enabled Token](https://github.com/himu007/KMD-CC-Token-Test-Guide#what-is-cc-enabled-token)  
[How would those assets move?](https://github.com/himu007/KMD-CC-Token-Test-Guide#how-would-those-assets-move)  
[Compile Komodo](https://github.com/himu007/KMD-CC-Token-Test-Guide/blob/master/README.md#compile-komodo)    
[Available RPC Commands](https://github.com/himu007/KMD-CC-Token-Test-Guide/blob/master/README.md#available-rpc-commands)  
[How to Create a New Contract?](https://github.com/himu007/KMD-CC-Token-Test-Guide/blob/master/How-to-create-a-new-contract.md)  
---
## [Frequently Aksed Questions (faq)](https://github.com/himu007/KMD-CC-Token-Test-Guide/blob/master/faq.md)  


## What is CC Enabled Token
We have core assets support to CC enabled coins. Still need to test it and make rpc calls to createasset and transferasset, but there is no GUI or high level tracking of such things. And no DEX for assets. Just experimenting with what can be done with CC.
An assetchain could now be used as a tokenizing platform. The tokens inherited the utxos. They are utxos, just special ones (colored coins actually).
These are assets, like NXT assets, or you can refer them as tokens. Tokenizing chain can be done within an assetchain. They can be generated from any chain with CC enabled.
It has no rpc yet, need to use hoek to create and transfer assets. But there would be rpc like: createasset, transferasset (will be like sendmany), assetaddress <pubkey> which returns a dedicated address where all assets for a pubkey end up.
Using an explorer (addressindex) then the assets balance for an address can be tallied.
It requires locking X amount of native coins to create the supply for an asset. So, if you want a unique asset, make it 1 satoshi. Using 1 coin gives you 100 million assets. Or you can interpret it with different decimal precision.
Each satoshi can be 1 token. So from 1.00000000 coins it makes 100 million assets, but without any fractions.

## How would those assets move?
It is still a ways to go from being done. `transferasset` rpc that works like `sendmany`. Well, you would need to specific the source txid/vout as it is critical to match outputs with inputs. If you send to burn address, it is burnt.
jl777 made good progress and am 90% code complete with the assets CC. Keep in mind the last 10% takes 90% of time, so still on pace for completion next week. However, assets include an asset exchange is likely bigger than most contracts (think erc20 + one of the ETH DEX projects combined) and this was my first CC contract.

```
create name:description -> txid for assetid
transfer <pubkey> <assetid> -> [{address:amount}, ... ] // like withdraw api
selloffer <pubkey> <txid/vout> <amount> -> cancel or fillsell -> mempool txid or rejected, might not confirm
buyoffer <amount> <assetid> <required> -> cancelbuy or fillbuy -> mempool txid or rejected, might not confirm
exchange <pubkey> <txid/vout> <required> <required assetid> -> cancel or fillexchange -> mempool txid or rejected, might not confirm
assetsaddress <pubkey> // all assets end up in a special address for each pubkey
assetbalance <pubkey> <assetid>
assetsbalances <pubkey>
asks <assetid>
bids <assetid>
swaps <assetid>
```

## Compile Komodo
```shell
cd ~
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python zlib1g-dev wget bsdmainutils automake libboost-all-dev libssl-dev libprotobuf-dev protobuf-compiler libgtest-dev libqt4-dev libqrencode-dev libdb++-dev ntp ntpdate nano software-properties-common curl libcurl4-gnutls-dev cmake clang

git clone https://github.com/nanomsg/nanomsg
cd nanomsg
cmake . -DNN_TESTS=OFF -DNN_ENABLE_DOC=OFF
make -j2
sudo make install
sudo ldconfig

cd ~
git clone https://github.com/jl777/komodo
cd komodo
git checkout dev
./zcutil/fetch-params.sh
./zcutil/build.sh -j$(nproc)
```

## Available RPC commands
```
== Tokens ==
tokenaddress [pubkey]
tokenask numtokens tokenid price
tokenbalance tokenid [pubkey]
tokenbid numtokens tokenid price
tokencancelask tokenid asktxid
tokencancelbid tokenid bidtxid
tokencreate name supply description
tokenfillask tokenid asktxid fillamount
tokenfillbid tokenid bidtxid fillamount
tokenfillswap tokenid otherid asktxid fillamount
tokenorders [tokenid]
tokenswap numtokens tokenid otherid price
tokentransfer tokenid destpubkey amount
faucetaddress [pubkey]
faucetfund 
amountfaucetget
```
