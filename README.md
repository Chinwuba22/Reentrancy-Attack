## Reentrancy Attack

Reentrancy Attack is a type of exploit wchich allows an exploter to repeatedly call a particular function. The Major cause of this attack is usually a failure to comply with the CEI(Checks, Effects, Interactions) principle or(and) failure to use a reentrant safeguard. An example of a reentrant safeguard can be:

```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract ReEntrancyGuard {
bool internal locked;

    modifier noReentrant() {
        require(!locked, "No re-entrancy");
        locked = true;
        _;
        locked = false;
    }

}
```

Protocols can also Use this Openzeppelin code as a nonRentrant guard: (https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/ReentrancyGuard.sol)

Since Reentrancy attack as said before is caused by majorly two factors, the best way to fight this problem is to always ensure to follow the CEI principle or(and) use a Reentrancy guard when interacting with external contract.

## TESTING

To test this contract simple run the following command:

1. Clone the Repo

```shell
git clone https://github.com/Chinwuba22/Reentrancy-Attack.git
```

2. Read and understand the contracts in `src` folder

3. Compile all file

```shell
forge build
```

or

```shell
forge compile
```

4. Read and understand the contracts in `test` folder

5. Run Test

```shell
forge test --match-test test_attackScenerio -vvv
```
