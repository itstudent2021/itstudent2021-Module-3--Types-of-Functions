// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// Importing the ERC20 standard implementation from OpenZeppelin
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.3.0/contracts/token/ERC20/ERC20.sol";
// Importing the Ownable contract from OpenZeppelin to manage ownership
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.3.0/contracts/access/Ownable.sol";

// Defining the contract
contract FinnToken is ERC20, Ownable {
    // Constructor to initialize the token with an initial supply
    constructor(uint256 initialSupply) ERC20("Finn", "FINN") {
        // Mint the initial supply to the contract deployer (owner)
        _mint(msg.sender, initialSupply);
    }

    // Function to mint new tokens, only accessible by the owner
    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    // Function to burn tokens, accessible by any user
    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    // Overriding the transfer function to use the _transfer internal function
    function transfer(address to, uint256 amount) public override returns (bool) {
        _transfer(_msgSender(), to, amount);
        return true;
    }
}
