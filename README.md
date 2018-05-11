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

## Steem transactions
Tbd

## Economics
### Fractional reserve
Each transaction contains 

### Fee based


## Light clients
Using blocks could be considered for data pruning. A system could also be setup where node producers periodically update a state hash that can be challanged when wrong.

VerSum may also be an option.


## Influences
* Counterparty
