Q: I can code my own smart contract in Go language and compile it to a library file (example .a file), and use that to compile with komodo source code?
A: As long as it compiles to a linkable library, the language for new contract (faucet.cpp equivalent) wont matter. It would need to be compatible with C/C++ stack calling convention. It is `komodod` that is doing all this. seems logical to extend `komodod`. It is a native contract, directly accessing the DB and datastructures. 

Q: 
A: 
