# Spec
Ethereum-on-steem uses embedded consensus to run ethereum using steem as a consensus layer. This repository serves as a rough specification.

## Steem Entrypoint
Steem can be used purely as a consensus mechanism but the contracts could interact with it more natively. This is undecided.

To interact with ethereum-on-steem, one will broadcast either a transfer or a transaction to steemit containing one of these operations:
- publish
- execute

Because the structure of a transfer memo is limited, (max 2kB, UTF-8), ipfs will be used to store the actual operation. 

The format for an operation could be something like `{"version": "0.0.1", "method": "execute", "params": {"gas_limit": 100000, "gas_price": 10, "data": {}, "address": "0x..", "signature": "signature", "nonce": 10}}`, where the params are hashed to ipfs.

## Virtual Machine
* https://github.com/ethereumjs/ethereumjs-vm

COINBASE opcode can be recycled for a different purpose (perhaps transfering the native token?).

The system will use ethereum addresses.

Interaction with the steem state should be considered (react to steem transfers...).

## Ethereum transfers
Transfer ether between the ethereum mainnet and eos.

Users will be able to lock their ether on the ethereum mainnet app. Once it is locked, they receive the same amount of ether on ethereum-on-steem. Holders of ether on eos can withdraw it back to the mainnet at any time.

Writing an ethereum mainnet relay on the eos mainnet will be easy (because POW is easy to proof), the other way around will be a lot more difficult. So an important question to ask is how to get ether back on the mainnet:
- A steemit relay by itself would still be insufficient (as we need to know whether or not a transaction is valid by the protocol)

["Light clients authenticate transactions using only the block headers and merkle proofs. EOS.IO will be the first proof-of-stake protocol with support for light client validation. More importantly, it will be the only one capable of generating proof-of-completeness. This means it will be possible to prove you have received all relevant prior messages from another chain in order without having a waiting/challenge period."](https://medium.com/eosio/eos-io-dawn-2-0-released-development-update-c19348eac3c7)

## Steem transactions
Tbd

## Economics
### Fractional reserve
Each transaction contains 

### Fee based


## Light clients
Using blocks could be considered for data pruning. A system could also be setup where node producers periodically update a state hash that can be challanged when wrong.

VerSum may also be an option.

[


## Influences
* Counterparty
