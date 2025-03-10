---
title: Flattening Smart Contract 
---

# Flattening Smart Contracts on the XDC Network

When a smart contract imports a contract that it depends on from another source, that top level smart contract and it's dependencies will have to be flattened before it can be verified on a block explorer.  This section explains how to flatten smart contracts using three different development toolchains; Remix, Truffle, and Hardhat.

For a good overview of flattening smart contracts on the XDC Network please refer to [this article](https://medium.com/@tivan7404/learn-how-to-flatten-a-smart-contract-and-verify-on-blocksscan-4daca3be3ac7).

# Flattening Smart Contracts with Remix
Remix IDE is one of the most user-friendly tools for smart contract development. To flatten a smart contract in Remix:

- **Develop Your Contract:** Write and compile your smart contract within the Remix environment.
- **Use the Flattener Plugin:** Remix provides a plugin called "Solidity Flattener" that you can easily activate from the plugin manager.
- **Generate the Flattened Code:** Once your contract is ready, run the flattener to generate a single file containing all your code dependencies.
This process is straightforward and ensures that your contract is ready for deployment on the XDC Network with minimal hassle.

**Refer to know in detail:** https://www.xdc.dev/ivan_blocksscan/learn-how-to-flatten-a-smart-contract-and-verify-on-blocksscan-56on

# Flattening Smart Contracts with Truffle
Truffle is another powerful tool for smart contract development that supports the XDC Network. The process involves:

- **Setup Your Truffle Project:** Initialize a Truffle project and write your smart contracts.
- **Install the Required Dependencies:** Use NPM or Yarn to install necessary libraries for flattening, such as truffle-flattener.
- **Run the Flattener:** Execute the truffle-flattener command in your terminal to merge your contracts into a single file.
This method is ideal for developers who prefer a more traditional development environment and want to ensure their contracts are fully prepared for deployment on the XDC Network.

**Refer to know in detail:** 

# Flattening Smart Contracts with Hardhat
Hardhat offers advanced tooling for smart contract developers and supports the XDC Network natively. The flattening process using Hardhat involves:

- **Initialize Hardhat:** Set up a new Hardhat project and write your contracts.
- **Install Flattening Tools:** Use the hardhat-flatten package to simplify the flattening process.
- **Execute the Flattening Command:** Run the flatten command in your terminal, and Hardhat will output a single file containing all the necessary code.
Hardhat's flexibility makes it an excellent choice for developers looking to deploy on the XDC Network, as it offers comprehensive tooling and support for complex smart contract workflows.

**Refer to know in detail:** https://www.xdc.dev/jay_kulkarni_842b41d81b23/deploying-and-verifying-a-pepe-token-on-the-xdc-network-using-hardhat-3nc7