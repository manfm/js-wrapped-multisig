# TON blockchain JS wrapped multisig contract

JS Interaction scripts for [multisig contract](https://github.com/akifoq/multisig).

## About
This repository contains simple Node.js code to deploy and interact with TON multisig wallet. This wallet needs to receive all signatures in one messages. Backend server is needed to facilitate signing for all signers.

## Instalation

```
yarn
cp .env.example .env
```
Make sure you have func installed.
Fift binaries come with package, you don't need to install them.

## Compilation

Compile the contract with `func -SPA stdlib.fc multisig-code.fc multisig-code.fif`.

Should this repository include compiled contract?

## Scripts

### Client side

generate you private key:

```
npm run client:generate-key ./data/key
```

Copy public key from terminal and send it to server side admin.

After server admin setups multisig smart contract, you are ready to submit transaction by running `npm run client:send-tx`.

Parameters are: receiving address, amount in TON, your public address, path to your private key.
Example:

```
npm run client:send-tx EQDzXdMc_F_1Ek4fzJEIe_CtVoRMdDOGL1OJSsT5Tma5XYHQ 0.1 PuZnMzx6J2E3obmLjtuQiBPbQrqFtEiKYg2+STwvp9i/ty7S ./data/key
```

### Server side

Copy all public addresses of signers to ./data/keys.pub

Prepare smart contract by running
`npm run multisig:create`.

Parameters are: k = minimum number of signatures.
Example:

```
npm run multisig:create 2
```
Fund bounceable address with some TON.
Deploy smart contract by running

```
npm run multisig:deploy
```

Deploy takes no parameters.

Run server

```
npm run server:start
```
