# KMD-CC-Token-Test-Guide
Komodo CC Token testing description, setup &amp; how-to

## Table of Contents  

[Compile Komodo](https://github.com/himu007/KMD-CC-Token-Test-Guide/blob/master/README.md#compile-komodo)    
[Available RPC Commands](https://github.com/himu007/KMD-CC-Token-Test-Guide/blob/master/README.md#available-rpc-commands)  
[(WIP) RPC Commands](https://github.com/himu007/KMD-CC-Token-Test-Guide/blob/master/README.md#wip-rpc-commands)  
[How to Create a New Contract?](https://github.com/himu007/KMD-CC-Token-Test-Guide/blob/master/How-to-create-a-new-contract.md)  

---
### [Frequently Aksed Questions (faq)](https://github.com/himu007/KMD-CC-Token-Test-Guide/blob/master/faq.md)  

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

## Available RPC Commands

[== Tokens ==](./rpc/token)  
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
tokeninfo 
tokenorders [tokenid]  
tokenswapask numtokens tokenid otherid price  
tokentransfer tokenid destpubkey amount  

[== Faucet ==](./rpc/faucet)  
faucetaddress [pubkey]  
faucetfund  
amountfaucetget  

## WIP RPC Commands
```
== Rewards ==
rewardsaddfunding name fundingtxid amount
rewardsaddress [pubkey]
rewardsfund name amount APR mindays maxdays mindeposit
rewardslock name fundingtxid amount
rewardsunlock name fundingtxid [txid]
```

## General guidance on reporting issues on discord (Regarding CryptoConditions development):

* the specific chain parameters so anyone can connect to it
* the **EXACT** rpc call and parameters you used
*  **the most important!** the raw tx generated
*  clear description of why you think it is a bug. for now you need to look at the raw tx details to make sure all vins are valid, signed and all vouts are sane.
* Please don't post things like "i tried X and it didnt work" as that does not help at all at this stage. These are raw transaction level things and until everything works, things won't work at the higher level.

## Suggested RPC Commands
```
WIP
```
