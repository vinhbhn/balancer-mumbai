# Guide to deploy on Mumbai

1. Contracts

- balancer-core have bFactory address

```
cd balancer-core
cp .env_example .env
yarn
npx truffle compile --all --network mumbai
npx truffle migrate --network mumbai
```

- balancer-core-v2 have Multicall address

```
cd balancer-core-v2
cp .env.example .env
yarn
npx hardhat --network mumbai compile
yarn run deploy:mumbai
```

- exchange-proxy have exchangeProxy address and Weth9 address

```
cd exchange-proxy
cp .env.example .env
yarn
npx truffle compile --all --network mumbai
npx truffle migrate --network mumbai
```

- bactions-proxy have bActions address and dsProxyRegistry(dsProxyFactory) address

```
cd bactions-proxy
cp .env.example .env
yarn
npx truffle compile --all --network mumbai
npx truffle migrate --network mumbai
```

Remember to save 5 addresses above.

2. Subgraph

```
cd balancer-subgraph
yarn
```

Fill in `subgraph.mumbai.yaml` with 5 addresses above.

Searching each address on [explorer](https://explorer-mumbai.maticvigil.com) to find block where contract creation, after that fill to startBlock.

Deploy subgraph on mumbai testnet

```
yarn run deploy:mumbai
```

3. UI

```
cd balancer-frontend
npm install
```

Create a file .env with

```
APP_CHAIN_ID=80001
APP_GAS_PRICE=100000000000
```
