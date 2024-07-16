## README

### ERC20 Token Contract

This repository contains a simple implementation of an ERC-20 token.

**Functions:**
- `totalSupply()`: Returns the total supply of tokens.
- `balanceOf(address account)`: Returns the balance of a specified account.
- `transfer(address recipient, uint amount)`: Transfers tokens to a specified address.
- `allowance(address owner, address spender)`: Returns the remaining number of tokens that the spender can spend.
- `approve(address spender, uint amount)`: Sets the allowance for a spender.
- `transferFrom(address sender, address recipient, uint amount)`: Transfers tokens on behalf of the owner.

**Events:**
- `Transfer`: Emitted when tokens are transferred.
- `Approval`: Emitted when an allowance is set.

### Vault Contract

The Vault contract allows users to deposit and withdraw ERC-20 tokens, minting and burning shares to track their balance.

**Functions:**
- `constructor(address _token)`: Initializes the Vault with the ERC-20 token address.
- `deposit(uint _amount)`: Deposits tokens into the Vault, minting shares.
- `withdraw(uint _shares)`: Withdraws tokens from the Vault, burning shares.

**License:**
This project is licensed under the MIT License.
