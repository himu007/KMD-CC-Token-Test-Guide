# Komodo Platform's CryptoConditions SmartContract development
Komodo CC Token testing description, setup &amp; how-to

## Available SmartContracts
Select the contract to learn more about the SmartContract from below.  
[Tokens](./rpc/token)  
[Rewards](./rpc/rewards)  
[Faucet](./rpc/faucet)  

## WIP SmartContracts
Dice
Lotto
Ponzi
Auction

## How to Start?
Compile Komodo, navigate to `src` dir, start the test chain with your pubkey and issue the SmartContract RPC commands to test. 
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
cd src
./komodod -ac_cc=1 -ac_name=ATEST -addressindex=1 -spentindex=1 -ac_supply=1000 -ac_reward=10000000000000 -pubkey=<yourpubkey> -addnode=136.243.58.134 -addnode=195.201.20.230 -addnode=195.201.137.5 &
```

## General guidance on reporting issues on discord (Regarding CryptoConditions and SmartContract development):

* the specific chain parameters so anyone can connect to it
* the **EXACT** rpc call and parameters you used
*  **the most important!** the raw tx generated
*  clear description of why you think it is a bug. for now you need to look at the raw tx details to make sure all vins are valid, signed and all vouts are sane.
* Please don't post things like "i tried X and it didnt work" as that does not help at all at this stage. These are raw transaction level things and until everything works, things won't work at the higher level.

## Suggested RPC Commands
```
WIP
```
---
### [Frequently Aksed Questions (faq)](https://github.com/himu007/KMD-CC-Token-Test-Guide/blob/master/faq.md)  
