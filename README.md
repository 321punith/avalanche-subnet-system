## README

# Vault Contract

This repository contains a smart contract for a Vault that interacts with ERC-20 tokens. The contract allows users to deposit and withdraw tokens, while minting and burning shares to represent their stake in the Vault.

### Table of Contents
- [Introduction](#introduction)
- [Contract Details](#contract-details)
- [Functions](#functions)
  - [Constructor](#constructor)
  - [Deposit](#deposit)
  - [Withdraw](#withdraw)
- [Events](#events)
- [License](#license)

## Introduction

The Vault contract is designed to manage deposits and withdrawals of ERC-20 tokens. Users can deposit tokens into the Vault and receive shares in return, representing their portion of the total Vault balance. When they withdraw, their shares are burned, and they receive the equivalent amount of tokens back.

## Contract Details

The contract is implemented in Solidity and utilizes the `IERC20` interface to interact with ERC-20 tokens. The main features include:
- Depositing tokens into the Vault.
- Withdrawing tokens from the Vault.
- Minting and burning shares to keep track of user balances.

## Functions

### Constructor

```solidity
constructor(address _token) {
    token = IERC20(_token);
}
```

The constructor initializes the contract with the address of the ERC-20 token that the Vault will manage.

### Deposit

```solidity
function deposit(uint _amount) external {
    uint shares;
    if (totalSupply == 0) {
        shares = _amount;
    } else {
        shares = (_amount * totalSupply) / token.balanceOf(address(this));
    }

    _mint(msg.sender, shares);
    token.transferFrom(msg.sender, address(this), _amount);
}
```

The `deposit` function allows users to deposit a specified amount of tokens into the Vault. The number of shares to mint is calculated based on the current total supply and the balance of tokens in the Vault. The user's shares are then updated, and the tokens are transferred to the Vault.

### Withdraw

```solidity
function withdraw(uint _shares) external {
    uint amount = (_shares * token.balanceOf(address(this))) / totalSupply;
    _burn(msg.sender, _shares);
    token.transfer(msg.sender, amount);
}
```

The `withdraw` function allows users to withdraw tokens from the Vault by specifying the number of shares to burn. The equivalent amount of tokens is calculated based on the current total supply and the balance of tokens in the Vault. The user's shares are then updated, and the tokens are transferred back to the user.

## Events

The contract uses the following events from the `IERC20` interface:

```solidity
event Transfer(address indexed from, address indexed to, uint value);
event Approval(address indexed owner, address indexed spender, uint value);
```

These events are emitted during token transfers and approvals.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
