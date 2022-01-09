# Fair Trade Coffee Supply Chain

Prove the authenticity of coffee using the Ethereum blockchain.

## Project Write-Up

### UML Diagrams

[Activity Diagram](./uml/Activity%20Diagram.png)<br>
[Sequence Diagram](./uml/Sequence%20Diagram.png)<br>
[State Diagram](./uml/State%20Diagram.png)<br>
[Data Modelling](./uml/Data%20Model%20Diagram.png)<br>

### Libraries

`Truffle`: Used for developing, testing, and deploying my smart contracts

The `Roles` library was used by different access control contracts for easy add and remove in the supply chain and check existence

`truffle-hd-wallet-provider` to sign transactions for addresses.

`web3` for implementing front end of application

### General Write-Up

#### Compiling contracts:

```
PS C:\Users\Djordje Dajkovic\Desktop\Blockchain nanodegree\Coffee supply chain\nd1309-Project-6b-Example-Template\project-6> truffle compile
Compiling .\contracts\coffeeaccesscontrol\ConsumerRole.sol...
Compiling .\contracts\coffeeaccesscontrol\DistributorRole.sol...
Compiling .\contracts\coffeeaccesscontrol\FarmerRole.sol...
Compiling .\contracts\coffeeaccesscontrol\RetailerRole.sol...
Compiling .\contracts\coffeeaccesscontrol\Roles.sol...
Compiling .\contracts\coffeebase\SupplyChain.sol...
Compiling .\contracts\coffeecore\Ownable.sol...
Writing artifacts to .\build\contracts
```

#### Migrating contracts(local):

```
PS C:\Users\Djordje Dajkovic\Desktop\Blockchain nanodegree\Coffee supply chain\nd1309-Project-6b-Example-Template\project-6> truffle migrate
Using network 'development'.

Running migration: 1_initial_migration.js
  Deploying Migrations...
  ... 0xad17b7d005320c2463b39bc1ac02d56d5ee3e91cb4baea189ea709e4489bada4
  Migrations: 0x715d334bb77a3c1c75b4338b020e1bce65794a88
Saving successful migration to network...
  ... 0x576350ae8f6755931ea60c69c28129ad0520651eb96d66c6d48f966ac054c1bc
Saving artifacts...
Running migration: 2_deploy_contracts.js
  Deploying FarmerRole...
  ... 0x930b9adcddd02cc743333ea54e4bceb736e8d11f1dbe299f5ede577291fd9af6
  FarmerRole: 0xfe58ee63694bb00c311469fa492d10db368dcb83
  Deploying DistributorRole...
  ... 0x3647828e9906b755a4eb9e425ce3415c44aabf2fcee90f0b76b0bec22df11d09
  DistributorRole: 0xcb156bbdd861bb6574fe224d2730d3681ae60ae1
  Deploying RetailerRole...
  ... 0x9e38e532cb7e7d6904f388089858ba175d44f27978235fb2c228f3b96ea67f61
  RetailerRole: 0x63b179049afffdbd3348a7ec7f1de4eddc862791
  Deploying ConsumerRole...
  ... 0x1e3e8c6324348c972c9324ce4febcac9a6e3acc72c335e70bb436ff5ce0e2818
  ConsumerRole: 0x3962d27c841030c22791c1c24f97619c727bd3c9
  Deploying SupplyChain...
  ... 0x01713506600b032af7b4c97f1ffa2a1a53038365f6bafb068c9a54703f26282b
  SupplyChain: 0x918548bc5125ee0e589b940da89bf35351577ee8
Saving successful migration to network...
  ... 0xea266e52097761b2bc8cd29778fc7fa2ded986d30657baf19d02812307aab8c6
Saving artifacts...
```

#### Testing contracts

```
PS C:\Users\Djordje Dajkovic\Desktop\Blockchain nanodegree\Coffee supply chain\nd1309-Project-6b-Example-Template\project-6> truffle test
Using network 'development'.

ganache-cli accounts used here...
Contract Owner: accounts[0]  0xcdb9663228b9a5ca2f1e06022e3534b225930e01
Farmer: accounts[1]  0xe8c3900d29c28888ec7c27f5d7fe26ff9019315a
Distributor: accounts[2]  0xb5dd734fc2b8a79cd3684460948046936bd12f78
Retailer: accounts[3]  0x3da5fcf94a9ca42134647d64ca059620381f49b1
Consumer: accounts[4]  0x58cd0645b104905b3ceefad57a4f565ea28aa20d


  Contract: SupplyChain
    √ Testing smart contract function harvestItem() that allows a farmer to harvest coffee (1117ms)
    √ Testing smart contract function processItem() that allows a farmer to process coffee (568ms)
    √ Testing smart contract function packItem() that allows a farmer to pack coffee (360ms)
    √ Testing smart contract function sellItem() that allows a farmer to sell coffee (426ms)
    √ Testing smart contract function buyItem() that allows a distributor to buy coffee (923ms)
    √ Testing smart contract function shipItem() that allows a distributor to ship coffee (440ms)
    √ Testing smart contract function receiveItem() that allows a retailer to mark coffee received (1129ms)
    √ Testing smart contract function purchaseItem() that allows a consumer to purchase coffee (985ms)
    √ Testing smart contract function fetchItemBufferOne() that allows anyone to fetch item details from blockchain (171ms)
    √ Testing smart contract function fetchItemBufferTwo() that allows anyone to fetch item details from blockchain (126ms)


  10 passing (6s)
```
#### Full Migrations Output on Rinkeby network

```
PS C:\Users\Djordje Dajkovic\Desktop\Blockchain nanodegree\Coffee supply chain\nd1309-Project-6b-Example-Template\project-6> truffle migrate --reset --network rinkeby
Using network 'rinkeby'.

Running migration: 1_initial_migration.js
  Replacing Migrations...
  ... 0x39dcb69c5da5a668b1323792337e20b2b7331dd1310144576a6e9459ae229254
  Migrations: 0xca2f7237267c7641d750d15a2d7d67e9cd8504dc
Saving successful migration to network...
  ... 0xff811629aec57415c6eb117992bbb024f4bc7c22983c98bcd4c23c40cc71373f
Saving artifacts...
Running migration: 2_deploy_contracts.js
  Replacing FarmerRole...
  ... 0xa816e268141b0b731e5a6d820f6af2ad15c5e986697cbe0ae9b587001454e9a8
  FarmerRole: 0x4a6a7d68ecea067d00fec86b12da2ef358cdd45d
  Replacing DistributorRole...
  ... 0x09f71916a6c44f46e12402cdea3ed4d10086442113a55cb1fe586db666a4d070
  DistributorRole: 0x254e0b36a1afe63927689e8afffa78a34f4a8a44
  Replacing RetailerRole...
  ... 0xe5b80a47dc29e9f11e4d77a194b612881bd5efb9cefb8d3b30a024c2d927e19a
  RetailerRole: 0xfd0ab09f18b9120b65bd822f5a1da56e04da343f
  Replacing ConsumerRole...
  ... 0x25fa315022fc12885ccfb6b0c2f9ca6b7aea0b2ac5e1cdbf45baa3c1cbfc319d
  ConsumerRole: 0xa14bdc4dcd140fe5e4920d0b6a7b5d37d0bc1af3
  Replacing SupplyChain...
  ... 0x0e587baf6f9fe971f19512fe6711a132a7e59964f110dd00f5b5840ebbf85738
  SupplyChain: 0x96c77849383db729cac0b21b81fed083b91d378e
Saving successful migration to network...
  ... 0x4a0eaa658d784f546d9c54bc2db367df97a9b0ea706bff8e523187ca2bdcefc3
Saving artifacts...
```
## Smart Contract

SupplyChain Tx hash: [0x4a0eaa658d784f546d9c54bc2db367df97a9b0ea706bff8e523187ca2bdcefc3](https://rinkeby.etherscan.io/tx/0x4a0eaa658d784f546d9c54bc2db367df97a9b0ea706bff8e523187ca2bdcefc3)<br>
SupplyChain Contract address: [0x96c77849383db729cac0b21b81fed083b91d378e](https://rinkeby.etherscan.io/address/0x96c77849383db729cac0b21b81fed083b91d378e)<br>

## Development Notes

Truffle v4.1.14<br>
Solidity v0.4.24 (solc-js)<br>
Node v16.13.1<br>
Web3.js v1.6.1<br>
