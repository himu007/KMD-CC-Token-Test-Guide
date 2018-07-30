## tokenfillask
Usage: `tokenfillask tokenid asktxid fillamount`

### Step 1: Create raw transaction
Example Command:
```shell
./komodo-cli -ac_name=ATEST tokenfillask 9217014eae0a83a0b64632f379c1b474859794f9eaf1cf1eecf5804ed6124a5e d1b2676bb118d7bb8604dc5bb0a320a2ffb6f7ee118bfd20ed33be3fbd0b9b62 50
```
Output: 
```JSON
totally filled!
{
  "result": "success",
  "hex": "01000000031a47a2fa94f27f7e98645a6827f9382991d76fcfd2d84b96065763d1cfed78fc02000000494830450221008be941e56b10fb51459f66288bb68936c55fd17ecbebd12b142f4575b0fe4bf702205f048ad69269ba81530230496fea42983aad88882b1ef7d08304e1230040fb0001ffffffff629b0bbd3fbe33ed20fd8b11eef7b6ffa220a3b05bdc0486bbd718b16b67b2d1000000007b4c79a276a072a26ba067a565802102adf84e0e075cf90868bd4e3d34a03420e034719649c41f371fc70d8e33aa27028140da534b773f52c77ebbd590330468ba49333acc0971da444de512b85d039f59f778c8bab7cb1be909b6473789b237966a0f137a9b24c93ebebe0d83ae34a6bd6fa100af038001e3a10001ffffffff2bf671abc3bdfb673c0103a3bd59282c1aee473c6ccc4b591cdb42dc469d68c4000000004847304402204fa686dfdc7c0b7d42e538751aee0534b54747df4f335fb4d3b0d1a86c68e96d02202083fa811dd4506ad83f6d58a420d31ff7ccbae84ea05399b616e3d6f373682401ffffffff050000000000000000302ea22c80201ab400e039122028345520ba041ac3e6ec81ad28d8415e78d760d55f41097dd58103120c008203000401cc3200000000000000302ea22c8020bc485b86ffd067abe520c078b74961f6b25e4efca6388c6bfd599ca3f53d8dae8103120c008203000401cc0065cd1d00000000232103fcc4b37ee767a67b75503832764b559d764d71c13785482b73609159aa6ae9efacf01710252d090000232103fe754763c176e1339a3f62ee6b9484720e17ee4646b65a119e9f6370c7004abcac00000000000000004f6a4c4ce3539217014eae0a83a0b64632f379c1b474859794f9eaf1cf1eecf5804ed6124a5e00000000000000002103fcc4b37ee767a67b75503832764b559d764d71c13785482b73609159aa6ae9ef00000000"
}
```

### Step 2: Broadcast the hex or sendrawtransaction
Example Command
```shell
$ ./komodo-cli -ac_name=ATEST sendrawtransaction 01000000031a47a2fa94f27f7e98645a6827f9382991d76fcfd2d84b96065763d1cfed78fc02000000494830450221008be941e56b10fb51459f66288bb68936c55fd17ecbebd12b142f4575b0fe4bf702205f048ad69269ba81530230496fea42983aad88882b1ef7d08304e1230040fb0001ffffffff629b0bbd3fbe33ed20fd8b11eef7b6ffa220a3b05bdc0486bbd718b16b67b2d1000000007b4c79a276a072a26ba067a565802102adf84e0e075cf90868bd4e3d34a03420e034719649c41f371fc70d8e33aa27028140da534b773f52c77ebbd590330468ba49333acc0971da444de512b85d039f59f778c8bab7cb1be909b6473789b237966a0f137a9b24c93ebebe0d83ae34a6bd6fa100af038001e3a10001ffffffff2bf671abc3bdfb673c0103a3bd59282c1aee473c6ccc4b591cdb42dc469d68c4000000004847304402204fa686dfdc7c0b7d42e538751aee0534b54747df4f335fb4d3b0d1a86c68e96d02202083fa811dd4506ad83f6d58a420d31ff7ccbae84ea05399b616e3d6f373682401ffffffff050000000000000000302ea22c80201ab400e039122028345520ba041ac3e6ec81ad28d8415e78d760d55f41097dd58103120c008203000401cc3200000000000000302ea22c8020bc485b86ffd067abe520c078b74961f6b25e4efca6388c6bfd599ca3f53d8dae8103120c008203000401cc0065cd1d00000000232103fcc4b37ee767a67b75503832764b559d764d71c13785482b73609159aa6ae9efacf01710252d090000232103fe754763c176e1339a3f62ee6b9484720e17ee4646b65a119e9f6370c7004abcac00000000000000004f6a4c4ce3539217014eae0a83a0b64632f379c1b474859794f9eaf1cf1eecf5804ed6124a5e00000000000000002103fcc4b37ee767a67b75503832764b559d764d71c13785482b73609159aa6ae9ef00000000
```
Output:  
```JSON
AssetValidate (S)
vin1 50, vout1 50, AssetValidateSellvin
Got 0.00000050 to origaddr.(RVCVaEHdH1gp1aPfu9MkgGBfdVNuW824PY)
0 0 50 50 500000000 500000000
got recvunitprice 0.10000000 >= 0.10000000 unitprice, new unitprice 0.00000000
fill validated
b6ebeaafced887fd63deb9207e0484570d49abe8fe4fcbaa026666d4ea3f902e
```

### Step 3: Wait for the tx to be confirmed!
