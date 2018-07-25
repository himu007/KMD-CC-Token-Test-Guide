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

**Q: What is the importance of the EVAL codes like in https://github.com/jl777/komodo/blob/jl777/src/cc/eval.h#L43 ?**

A: EVAL codes in eval.h are the CC contract-type ID. e.g. "rewards contract" ID is 0xe5, faucet contract is 0xe4.  The goal is to have building blocks of smart contracts.  The smart contract "library" or "catalogue" is available to all of komodo.  You pick what you need to use for your use of blockchain.   If you need something different, you pick the "smart contract of closest fit" and make your changes.  If you want, you PR it upstream back to komodo and it is included in the komodo "catalogue of smart contracts".

**Q: Can you chain together contracts like IF statements?**

A: As at July 2018, The demo contracts currently use the absolute simplest possible CC condition.  With that the developer is able to do assets, rewards, faucet and more.  There is no reason you cant make a contract that knows about other contracts.  If you can describe what the contract does in terms of utxo, likely it can be done as long as you dont require the __mindreading api__.  That is where it somehow magically needs to know what the user is thinking. Too many bugs with that one so far :)

**Q: What can a Komodo Smart Contract access on the blockchain?**

A: I dont think any other bitcoin protocol blockchain has contracts code with full access to prior blockchain data.

**Q:  Does each additional contract require a hard fork?**  

A: It depends on what you mean, how it was deployed and if any specific CC contracts were done.

Q:  

A:  


### Didn't find your answer here? Please ask question in #crypto-conditions channel in [Komodo Discord](https://komodoplatform.com/discord)
