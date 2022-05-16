# eth-bsc-bridge-adapter
ETH to BSC or BSC to ETH Cross Bridge Adapter, including Burning and Minting Template

PS. Use it with filled ETH/Rinkeby and BSC testnet faucets for testing.

https://faucet.rinkeby.io/

https://testnet.binance.org/faucet-smart


> npm install


Bridge contract on ETH

> truffle migrate --reset --network ethTestnet


Bridge contract on BSC


> truffle migrate --reset --network bscTestnet


Ok we have both smart contracts bridges on ETH and BSC
Now lets check the token balances on ETH and BSC networks.

ETH Network balance (which should be 1000 ref:scripts/eth-bsc-transfer.js line 6)

> truffle exec scripts/eth-token-balance.js --network ethTestnet 

BSC Network balance (which should be 0)

> truffle exec scripts/bsc-token-balance.js --network bscTestnet


Open a new terminal to build the bridge between networks, its going to listen transactions (currently no .env its hardcode. Be sure the you are on the right network!)

Listening from bridge contract on the ETH 

> node scripts/eth-bsc-bridge.js

Create transaction from another terminal:

> truffle exec scripts/eth-bsc-transfer.js --networkTestnet

You should see the bridge api is going to detect the transaction event on previous terminal
Which means its burned on ETH and minted on BSC and the tokens are now available.


Summarize and checking the current balances

ETH Network Balance should be 0

> truffle exec scripts/eth-token-balance.js --network ethTestnet

BSC Network Balance should be 1000

> truffle exec scripts/bsc-token-balance.js --network bscTestnet


All done,
Cheers.

@denizumutdereli