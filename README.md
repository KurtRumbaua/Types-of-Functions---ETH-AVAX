# GoCoin Token Contract

GoCoin is a custom ERC20 token implemented using Solidity. This smart contract allows for minting and burning of tokens, with ownership control for minting operations.

## Description

The GoCoin contract is built on the OpenZeppelin library, inheriting from the ERC20 and Ownable contracts. It initializes with a specified name, symbol, initial supply of tokens, and the initial owner's address. The contract provides functionality for the owner to mint new tokens and for any holder to burn their tokens.

## Getting Started

### Executing program

To deploy and interact with this contract, you can use Remix IDE.

1. **Open Remix IDE**: Go to [Remix IDE](https://remix.ethereum.org/).

2. **Create a new file**: Click on the "File Explorers" tab and create a new file named `GoCoin.sol`.

3. **Paste the contract code**: Copy the following code and paste it into the `GoCoin.sol` file.

   ```solidity
   // SPDX-License-Identifier: MIT
   pragma solidity ^0.8.0;
   
   import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
   import "@openzeppelin/contracts/access/Ownable.sol";
   
   contract GoCoin is ERC20, Ownable {
       constructor(string memory name, string memory symbol, uint256 initialSupply, address initialOwner)
           ERC20(name, symbol)
           Ownable(initialOwner) // Pass initialOwner to Ownable constructor
       {
           _mint(initialOwner, initialSupply);
       }
   
       function mint(address to, uint256 amount) public onlyOwner {
           _mint(to, amount);
       }
   
       function burn(uint256 amount) public {
           _burn(msg.sender, amount);
       }
   
       function transfer(address recipient, uint256 amount) public override returns (bool) {
           return super.transfer(recipient, amount);
       }
   }


4. **Compile the contract**: Go to the "Solidity Compiler" tab, select the appropriate compiler version (^0.8.0), and click "Compile GoCoin.sol".
5. **Deploy the contract**: Go to the "Deploy & Run Transactions" tab, select "Injected Web3" or "JavaScript VM" as the environment, and deploy the contract with the required parameters (name, symbol, initial supply, and initial owner address).

## Authors
Kurt Ian Rumbaua (kirrumbaua@mymail.mapua.edu.ph)

## License 
This project is licensed under the MIT License - see the LICENSE.md file for details.
