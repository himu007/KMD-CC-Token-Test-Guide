## Dice Smart Contract


### Available RPC calls

==Dice==
diceaddfunds name fundingtxid amount  
diceaddress [pubkey]  
dicebet name fundingtxid amount odds  
dicefund name funds minbet maxbet maxodds timeoutblocks  
diceinfo fundingtxid  
dicelist  
diceloser name fundingtxid bettxid  
dicerefund name fundingtxid bettxid  
dicewinner name fundingtxid bettxid  

but additionally, you need to create txids with hashed entropy, basically any dice tx other than a dicebet will add hashed entropy, but you need to create a few at first via diceaddfunds
the diceinfo, dicelist, diceaddress work just like the rewards counterparts
once there is a dice plan with funds, you can make dicebets. for now to resolve it the creator of the diceplan needs to do a dicewinner or diceloser
last I will add a dicerefund that allows anybody to undo a dicebet, this would happen only if the diceplan node is offline.I guess it could be that it refunds or it becomes an automatic win. not sure which is best. probably need to make it an automatic win to incentivize the "house" account not to go offline
in order to save a step, I dont hash the entropy of the dicebet. but I guess I need to if we want it to refund after timeout instead of automatic win, as the way it is now would allow the house account to just not complete a large losing bet
as you can see, things are not quite settled, but enough seems to work I wanted to get some feedback
