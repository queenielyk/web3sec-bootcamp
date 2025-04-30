# Notes

-   [Solidity](https://book.getfoundry.sh/)

## Set up Private Key

### load private key from env

[terminal] source .env
[code] uint256 deployerPrivateKey = vm.envUint("PRIVATE_KEY");

### import the private key into an encrypted keystore

```bash
cast wallet import <account_name> --interactive
forge script <name_of_script> --rpc-url $<name_of_rpc_url> --account <account_name>
```

`--broadcast` | broadcast the transaction

## RPC URL

An endpoint that enables to communicate with a blockchain

-   [Alchemy](https://www.alchemy.com/)
-   [ChainList](https://chainlist.org/chain/11155111)
-   [Infura](https://www.infura.io/zh)

### Request Testnet ETH

#### Sepolia Faucet

-   https://www.alchemy.com/faucets/ethereum-sepolia
-   https://www.infura.io/faucet/sepolia

## Commonly Used `cast` Commands

|                     |                                                                         |
| ------------------- | ----------------------------------------------------------------------- |
| `cast 4byte`        | get the function signature                                              |
| `cast 4byte-decode` | decode ABI-encoded calldata                                             |
| `cast balance`      | get the balance of an account in wei                                    |
| `codesize`          | get the runtime bytecode size of a contract                             |
| `cast estimate`     | estimate the gas cost of a transaction                                  |
| `cast run`          | run a published transaction in a local environment and prints the trace |
| `cast storage`      | get the raw value of a contract'storage slot                            |
| `cast to-hex`       | convert a number of one base to another                                 |
| `cast to-dec`       | convert a number of one base to decimal                                 |
| `cast tx`           | get information about a transaction                                     |

```bash
# extract function selectors and arguments (even from unverified bytecode)
cast sel -r $(cast code <code> -r $MAINNET_NODE_RPC_URL)
```

```bash
# analyze onchain tx in debugger
cast run <code> -r $MAINNET_NODE_RPC_URL -t
```

```bash
# create a vanity address
# vanity address: a custom wallet address created using specific algo
# ! address poisoning scam
cast wallet vanity <flags> <target_address>
```

## `anvil` CLI Tool

```bash
# create a local testnet node
anvil
anvil --fork-url $MAINNET_NODE_RPC_URL
```

## `chisel` CLI Tool

Run Solidity code snippets in REPL(Read-Eval-Print Loop) environment - an interactive environment

```bash
chisel

# example
➜ bytes memory s = hex"1234";
➜ !memdump
[0x00:0x20]: 0x0000000000000000000000000000000000000000000000000000000000000000
[0x20:0x40]: 0x0000000000000000000000000000000000000000000000000000000000000000
[0x40:0x60]: 0x00000000000000000000000000000000000000000000000000000000000000c0
[0x60:0x80]: 0x0000000000000000000000000000000000000000000000000000000000000000
[0x80:0xa0]: 0x0000000000000000000000000000000000000000000000000000000000000002
[0xa0:0xc0]: 0x1234000000000000000000000000000000000000000000000000000000000000
# 1st - 4th are fixed!
# 5th represents the valid length in bytes
# 6th represents address value
```
