## Requirements to Create New Contract

Pre-requisites: [Install Komodo](https://github.com/himu007/KMD-CC-Token-Test-Guide)

Source repo: https://github.com/jl777/komodo
Source directory: https://github.com/jl777/komodo/tree/dev/src/cc
Useful Links: https://raw.githubusercontent.com/jl777/komodo/dev/src/cc/assets.cpp

1. Add EVAL_CODE to eval.h
2. Initialize the variables in the CCinit function below
3. Write a Validate function to reject any unsanctioned usage of vin/vout
4. Make helper functions to create rawtx for RPC functions
5. Add rpc calls to rpcserver.cpp and rpcserver.h and in one of the rpc.cpp files
6. Add the new .cpp files to src/Makefile.am

1, 2 and 6 are not even coding tasks.
4 and 5 are non-consensus time, mostly dealing with JSON.
3 is the main work needed, which makes sense as a different 3 is what makes it a different contract.
A lot of a contract can use slightly modified functions from the other CC contracts. So the best way to do a new one would be to pick the one that is closest to what you want and start morphing it.

