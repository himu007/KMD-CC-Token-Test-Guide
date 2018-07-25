**Q: Can I code my own smart contract in Go language and compile it to a library file (example .a file), and use that to compile with komodo source code?**  
A: As long as it compiles to a linkable library, the language for new contract (faucet.cpp equivalent) wont matter. It would need to be compatible with C/C++ stack calling convention. It is `komodod` that is doing all this. seems logical to extend `komodod`. It is a native contract, directly accessing the DB and datastructures. 

**Q: What exactly the purpose of these addresses that are in the source code, with privkeys?  I just imported RFYE2yL3KknWdHK6uNhvWacYsCUtwzjY3u on test chain ATEST and spent the .0001 that was in it.**

A: you can only spend the normal funds in those addresses, CC outputs are protected CC addresses map the CC scriptPubKey to an address, not the pubkey the purpose of the addresses are to have special addresses that all nodes have the privkey for and are able to sign the CC transaction to released otherwise locked funds.

**Q: what's the purpose of sending coins to these addresses that are in the src code?**

A: depends on the CC contract
 - for the faucet contract, the purpose is to have funds for the faucet
 - for the assets contract, the purpose is to create colored coins
 - for the rewards contract, the purpose is to have funds for the rewards
 - etc
contracts usually needs to have funds to operate.

Q:  
A: 


### Didn't find your answer here? Please ask question in #crypto-conditions channel in [Komodo Discord](https://komodoplatform.com/discord)
