## Introduction

Foundry is completely Solidity based. Deploy scripts, tests, etc. are all written in Solidity.

[Foundry Docs](https://book.getfoundry.sh/)
[Cyfrin Github 1](https://github.com/Cyfrin/foundry-full-course-cu#foundry-fundamentals-section-1-foundry-simple-storage)
[Cyfrin Github 2](https://github.com/Cyfrin/foundry-simple-storage-cu)

Foundry pros:

- It **leverages Rust** for compilation, offering significantly faster build times compared to frameworks like Hardhat or Brownie.
- It's entirely **Solidity-based**, eliminating the need to learn other programming languages
- Its **documentation is comprehensive**

## Installation

[VS Code Keyboard Shortcuts](https://code.visualstudio.com/docs/getstarted/keybindings)

(I have already installed VS Code and WSL)

## Local Foundry Setup

Installed Foundry running:

`curl -L https://foundry.paradigm.xyz | bash`

Run `foundryup` to install Foundry for the 1st time or update to the latest version.

This install the 4 main components:

- forge
- cast
- anvil
- chisel

Vasily Gualoto explains how to generate an SSH key and add it to Github, so that you can clone repos using SSH.

## VS Code Setup

`CTRL + J` toggles the terminal panel and the rest of the tools in the panel.

## Create a new Foundry project (simple storage)

`forge init`

In the code installed:

- `lib` is the folder where all your dependencies are installed, you'll find things like:
  - `forge-std` (the forge library used for testing and scripting)
  - `openzeppelin-contracts` is the most battle-tested library of smart contracts
- `scripts` is a folder that houses all your scripts
- `src` is the folder where you put all your smart contracts
- `test` is the folder that houses all your tests
- `foundry.toml` gives configuration parameters for Foundry

## VSCode Solidity Setup

Install the Nomic Foundation Solidity extension.

## Compile a smart contract using Foundry

Run `forge build` or `forge compile` to compile your contracts.

When you do this, you get a `out/ContractName.json` file with a lot of relevant information, like the ABI, bytecode, etc.

## Deploy a smart contract locally using Anvil

Run `anvil` to get a local blockchain with **10 fake available accounts, their private keys** and an **RPC URL**.

Instructions about how to add your localhost RPC URL to Metamask.

Anvil's Chain ID is 31337.

While you are running Anvil, you can select one of the private keys for the given accounts, import it into Metamask and you'll see your balance inside there.

In these docs, you can see all the methods that Ethereum (and most EVM compatible) blockchain nodes can make.

[JSON-RPC](https://ethereum.org/en/developers/docs/apis/json-rpc/)
[Ethereum JSON-RPC Specification](https://ethereum.github.io/execution-apis/api-documentation/)

**NOTE**: Under the hood, forge is taking care of calling all these methods for us, but you could call these methods directly using a different language and script like bash or JavaScript.

## Deploy a smart contract locally using Forge

`forge create SimpleStorage --rpc-url http://127.0.0.1:8545 --interactive`

This will prompt us for our private key. I'll take the 1st of the ones given by Anvil, paste it (nothing actually shows but you click enter) and you get the following back:

```
Deployer: 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266
Deployed to: 0x5FbDB2315678afecb367f032d93F642f64180aa3
Transaction hash: 0xe933149cbe9c0958a21367bbf2f30a26dcdb497bcb22da9642c2059a71907cf8
```

If you are working with Anvil you can skip the rpc url:

`forge create SimpleStorage --interactive`

**NEVER PASTE THE PRIVATE KEY, i.e. NEVER DO THIS:**

`forge create SimpleStorage --private-key 0xabcdef100abc0d23abc0...etc`

## Deploy using a Script

In real life we won't be deploying contracts profesionally from the command line but rather running a script that we can test and make sure its safe.

Create `script/DeploySimpleStorage.s.sol` (the .s is a Foundry convention for scripts).

Read these [best practices](https://book.getfoundry.sh/tutorials/best-practices#scripts) for writing scripts.

Now we will tap into Foundry's standard library to indicate that we are writing a script in Solidity:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity 0.8.19;

import {Script} from "forge-std/Script.sol" // We import Script from the std library
import {SimpleStorage} from "../src/SimpleStorage.sol" // We import our contract to deploy

contract DeploySimpleStorage is Script {

}
```

In every deploy script we need a main function called `run`.
Now that we imported `Script` from `forge-std` we can make use of `vm.startBroadcast()` and `vm.stopBroadcast()`. Everything in between these 2 will be sent to the blockchain. The reason we use this, is because maybe we want to add some boilerplate or setup code and we don't want to spend gas on doing so, so we would add that code before `vm.startBroadcast()`.

```solidity
// SPDX-License-Identifier: MIT

pragma solidity 0.8.19;

import {Script} from "forge-std/Script.sol";
import {SimpleStorage} from "../src/SimpleStorage.sol";

contract DeploySimpleStorage is Script {
    function run() external returns (SimpleStorage) {
        vm.startBroadcast();
        SimpleStorage simpleStorage = new SimpleStorage();
        vm.stopBroadcast();
        return simpleStorage;
    }
}
```

Now to run this we do:

`forge script script/DeploySimpleStorage.s.sol`

Once we run this we get:

```
[⠊] Compiling...
[⠘] Compiling 20 files with Solc 0.8.19
[⠃] Solc 0.8.19 finished in 707.44ms
Compiler run successful!
Script ran successfully.
Gas used: 338569

== Return ==
0: contract SimpleStorage 0x90193C961A926261B756D1E5bb255e67ff9498A1

If you wish to simulate on-chain transactions pass a RPC URL.
```

Bear in mind this didn't use Anvil, this just created an on-the-fly simulated blockchain to deploy this to, and tore it down immediatly after finishing the deploy.

Now, if we are running Anvil we can do:

`forge script script/DeploySimpleStorage.s.sol --rpc-url http://127.0.0.1:8545`

And this actually gives us a more complete simulation of sending this to a blockchain:

```
Script ran successfully.

== Return ==
0: contract SimpleStorage 0x34A1D3fff3958843C43aD80F30b94c510645C316

## Setting up 1 EVM.

==========================

Chain 31337

Estimated gas price: 2.000000001 gwei

Estimated total gas used for script: 464097

Estimated amount required: 0.000928194000464097 ETH

==========================

SIMULATION COMPLETE. To broadcast these transactions, add --broadcast and wallet configuration(s) to the previous command. See forge script --help for more.

Transactions saved to: .../foundry-simple-storage/broadcast/DeploySimpleStorage.s.sol/31337/dry-run/run-latest.json

Sensitive values saved to: .../foundry-simple-storage/cache/DeploySimpleStorage.s.sol/31337/dry-run/run-latest.json
```

You can see a lot of information about the transaction that just took place in:

`/broadcast/DeploySimpleStorage.s.sol/31337/dry-run/run-latest.json`

To actually deploy to a blockchain you would run **BUT NEVER WITH A REAL PRIVATE KEY**:

`forge script script/DeploySimpleStorage.s.sol --rpc-url http://127.0.0.1:8545 --broadcast --private-key 0xabcdef100abc0d23abc0...etc`

And now we also get this:

```
==========================

##### anvil-hardhat
✅  [Success]Hash: 0x775312b009f79b11c37620c31a0621f80e587f6ea340ab89a764526a3ac72efb
Contract Address: 0x5FbDB2315678afecb367f032d93F642f64180aa3
Block: 1
Paid: 0.000357088000357088 ETH (357088 gas * 1.000000001 gwei)

✅ Sequence #1 on anvil-hardhat | Total Paid: 0.000357088000357088 ETH (357088 gas * avg 1.000000001 gwei)


==========================

ONCHAIN EXECUTION COMPLETE & SUCCESSFUL.
```

## What is a transaction

Foundry saves all your blockchain interactions in the `broadcast` folder. The `dry-run` folder is used for interactions you made when you didn't have a blockchain running.

In our `run-latest.json` file, we can find the transaction info:

```
"transaction": {
  "from": "0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266",
  "gas": "0x714e1",
  "value": "0x0",
  "input": "0x6080...3", // redacted for brevity
  "nonce": "0x0",
  "chainId": "0x7a69"
},
```

Let's see the fields:

- `from`: it's the address we used to sign the transaction
- `to`: This field doesn't show up when deploying a new contract
- `gas`: The gas spent in hex value.
- `value`: The amount of ETH we are sending over
- `input`: (data) is the contract deployment code and contract code.
- `nonce`: is a unique identifier assigned to each transaction sent from a specific account. It is incremented with every single transaction. The nonce can be used to prevent replay attacks.

In the [Ethereum docs](https://ethereum.org/en/developers/docs/transactions/) we can see that there are other fields like `signature`, but these details are abstracted away by Foundry in this case.

**ASIDE**: We can convert between hex and decimal numbers with cast:

`cast --to-base 0x714c2 dec`
