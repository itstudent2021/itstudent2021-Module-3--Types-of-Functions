# Module-3--Types-of-Functions

## FinnToken: An ERC20 Token Implementation

## Simple Overview
FinnToken is an ERC20 token implemented using the OpenZeppelin library. The token allows the contract owner to mint new tokens, while any user can transfer and burn tokens. This contract is designed to be deployed and interacted with using Remix IDE.

## Description
FinnToken is a smart contract that adheres to the ERC20 token standard, ensuring compatibility with various wallets and exchanges. The primary purpose of this token is to demonstrate the creation, minting, burning, and transferring of tokens on the Ethereum blockchain. Using the OpenZeppelin library, FinnToken leverages well-tested and secure code to provide standard functionalities. The owner of the contract has exclusive rights to mint new tokens, adding them to the total supply. However, any user can transfer their tokens to others or burn them, reducing the total supply.

## Getting Started

### Installing and Executing the Program

1. **Open Remix IDE:**
    - Go to [Remix IDE](https://remix.ethereum.org).

2. **Create a New File:**
    - Create a new file named `FinnToken.sol`.
    - Copy and paste this code` into the new file.
      
  ```solidity
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
  ```

3. **Compile the Contract:**
    - Click on the "Solidity Compiler" tab on the left sidebar.
    - Select the compiler version 0.8.0 or higher.
    - Click on the "Compile FinnToken.sol" button.

4. **Deploy the Contract:**
    - Click on the "Deploy & Run Transactions" tab on the left sidebar.
    - Enter the initial supply value (e.g., 1000).
    - Click on the "Deploy" button.

5. **Interact with the Contract:**
    - After deployment, the contract functions will be available in the "Deployed Contracts" section.
    - **Mint Tokens:** Only the contract owner can call the mint function. Provide the address and the amount to mint tokens.
    - **Burn Tokens:** Any user can call the burn function to burn their tokens.
    - **Transfer Tokens:** Any user can transfer tokens by calling the transfer function with the recipient's address and the amount.

### Functionality
- **Mint Tokens:** The contract owner can mint new tokens to any provided address using the mint function.
- **Burn Tokens:** Any user can burn their tokens using the burn function.
- **Transfer Tokens:** Any user can transfer tokens to another address using the transfer function.

## Help
### Common Issues and Solutions
- **Compilation Errors:** Ensure that the Solidity compiler version is set to 0.8.0 or higher.
- **Deployment Failures:** Make sure the initial supply value is a positive integer and the account has sufficient gas.
- **Function Calls Failing:** Ensure that you are logged in with the correct account (contract owner for minting).

For more detailed assistance, refer to the [OpenZeppelin Documentation](https://docs.openzeppelin.com/).

## Authors
-Itstudent2021

## License

This project is licensed under the MIT License - see the `LICENSE.md` file for details
