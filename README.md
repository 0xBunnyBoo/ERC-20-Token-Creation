ERC20-Token-Creation/
│
├── contracts/
│   └── MyToken.sol
│
├── migrations/
│   └── 1_initial_migration.js
│   └── 2_deploy_contracts.js
│
├── test/
│   └── MyToken.test.js
│
├── scripts/
│   └── deploy.js
│
├── .gitignore
├── README.md
├── truffle-config.js
└── package.json
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("MyToken", "MTK") {
        _mint(msg.sender, initialSupply);
    }
}
const Migrations = artifacts.require("Migrations");

module.exports = function (deployer) {
  deployer.deploy(Migrations);
};
const MyToken = artifacts.require("MyToken");

module.exports = function (deployer) {
  const initialSupply = 1000000; // Initial supply of tokens
  deployer.deploy(MyToken, initialSupply);
};
const MyToken = artifacts.require("MyToken");

contract("MyToken", (accounts) => {
  it("should put 1000000 MTK in the first account", async () => {
    const instance = await MyToken.deployed();
    const balance = await instance.balanceOf(accounts[0]);
    assert.equal(balance.valueOf(), 1000000, "1000000 wasn't in the first account");
  });
});
async function main() {
  const [deployer] = await ethers.getSigners();
  console.log("Deploying contracts with the account:", deployer.address);

  const MyToken = await ethers.getContractFactory("MyToken");
  const myToken = await MyToken.deploy(1000000);

  console.log("Token deployed to:", myToken.address);
}

main()
  .then(() => process.exit(0))
  .catch((error) => {
    console.error(error);
    process.exit(1);
  });
node_modules
build
.env
# ERC-20 Token Creation

This project demonstrates how to create an ERC-20 token on the Ethereum blockchain using Solidity and Truffle.

## Prerequisites

- Node.js
- Truffle
- Ganache (for local development)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/ERC20-Token-Creation.git
   cd ERC20-Token-Creation
npm install
truffle compile
truffle migrate
truffle test
truffle migrate --network <network_name>

#### 8. `truffle-config.js`
```javascript
module.exports = {
  networks: {
    development: {
      host: "127.0.0.1",
      port: 7545,
      network_id: "*", // Match any network id
    },
  },
  compilers: {
    solc: {
      version: "0.8.0",
    },
  },
};
{
  "name": "erc20-token-creation",
  "version": "1.0.0",
  "description": "A project to create an ERC-20 token on Ethereum",
  "main": "truffle-config.js",
  "scripts": {
    "test": "truffle test"
  },
  "author": "Your Name",
  "license": "MIT",
  "dependencies": {
    "@openzeppelin/contracts": "^4.0.0",
    "truffle": "^5.0.0",
    "web3": "^1.0.0"
  },
  "devDependencies": {
    "chai": "^4.2.0",
    "mocha": "^8.0.0"
  }
}
