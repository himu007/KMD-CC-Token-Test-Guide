# KMD-CC-Token-Test-Guide
Komodo CC Token testing description, setup &amp; how-to

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
