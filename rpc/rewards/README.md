## What is rewards contract?
Rewards CC allows to create a master-node like rewards program. Which gives the user the ability to earn rewards by locking coins.  
APR and mindeposit are configurable per rewards plan (there can be many active at any given time), even the required holding period.

## Available RPC Calls
```
== Rewards ==
rewardsaddfunding name fundingtxid amount
rewardsaddress [pubkey]
rewardscreatefunding name amount APR mindays maxdays mindeposit
rewardsinfo fundingtxid
rewardslist
rewardslock name fundingtxid amount
rewardsunlock name fundingtxid [txid]
```

