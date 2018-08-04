## Dice Smart Contract


### Available RPC calls

==Dice==  
[diceaddfunds name fundingtxid amount](./diceaddfunds.md)  
[diceaddress [pubkey]](./diceaddress.md)  
[dicebet name fundingtxid amount odds](./dicebet.md)  
dicefinish name fundingtxid bettxid  
[dicefund name funds minbet maxbet maxodds timeoutblocks](./dicefund.md)  
[diceinfo fundingtxid](./diceinfo.md)  
[dicelist](./dicelist.md)  
dicestatus name fundingtxid bettxid
dingtxid
dicelist

Additionally, you need to create txids with hashed entropy, basically any dice tx other than a dicebet will add hashed entropy, but you need to create a few at first via diceaddfunds
the diceinfo, dicelist, diceaddress work just like the rewards counterparts
once there is a dice plan with funds, you can make dicebets. for now to resolve it the creator of the diceplan needs to do a dicewinner or diceloser
last I will add a dicerefund that allows anybody to undo a dicebet, this would happen only if the diceplan node is offline.I guess it could be that it refunds or it becomes an automatic win. not sure which is best. probably need to make it an automatic win to incentivize the "house" account not to go offline
in order to save a step, I dont hash the entropy of the dicebet. but I guess I need to if we want it to refund after timeout instead of automatic win, as the way it is now would allow the house account to just not complete a large losing bet
as you can see, things are not quite settled, but enough seems to work I wanted to get some feedback

the dicefund creator can actually finalize any dicebet transactions and it should properly deal with paying winners and not paying losing tx
