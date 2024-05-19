# MyToken Solidity Contract

**Author:** Cherrie Anne Sandrino, Student at NTC

## Introduction

This project implements a simple Solidity smart contract for a token named "MyToken". The contract includes functions for minting new tokens, burning tokens, and keeping track of the total supply and individual balances. This project serves as an introduction to basic token management on the Ethereum blockchain.

## Code Explanation

### Solidity Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {

    // Public variables to store token details
    string public name = "MyToken"; // Token name
    string public symbol = "MTK";   // Token abbreviation
    uint256 public totalSupply;     // Total supply of tokens

    // Mapping to store balances of addresses
    mapping(address => uint256) public balances;

    // Mint function to create new tokens
    function mint(address _to, uint256 _value) public {
        require(_to != address(0), "Invalid address");

        totalSupply += _value;        // Increase total supply
        balances[_to] += _value;      // Increase balance of the specified address
    }

    // Burn function to destroy tokens
    function burn(address _from, uint256 _value) public {
        require(_from != address(0), "Invalid address");
        require(balances[_from] >= _value, "Insufficient balance to burn");

        totalSupply -= _value;        // Decrease total supply
        balances[_from] -= _value;    // Decrease balance of the specified address
    }
}
