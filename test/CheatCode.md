# Cheat Code

## Execute Test

```bash
forge test --match-contract <name_of_test_module> -vvvvv
forge test --match-test <name_of_test_function> -vvvvv
forge test --debug <name_of_test_function>
forge test --mt <name_of_test_function> -vvvvv --decode-internal
forge test --mc <name_of_test_module> -vvvvv --gas-report
```

## Solidity Test Code

```solidity
vm.startPrank(msgSender, txOrigin) /
vm.prank() /
vm.stopPrank()
```

```solidity
v,.stopBroadcast([, signer, privateKey]) /
vm.broadcast() /
vm.stopBroadcast()
```

```solidity
vm.deal(account, newBalance)
```

```solidity
vm.roll(newHeight): Sets `block.height`
```

```solidity
wm.wrap(newTimestamp): Sets `block.timestamp`
```

```solidity
vm.expectEmit()
```

```solidity
vm.expectRevert()
```

```solidity
vm.createSelectFork(): Fork chain
```

```solidity
vm.envUnit()
```

```solidity
makeAddr(name)
```
