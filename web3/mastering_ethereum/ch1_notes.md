# What Is Ethereum?

From a computer science perspective, Ethereum is a deterministic but practically unbounded state machine, consisting of a globally accessible singleton state and a virtual machine that applies changes to that state.

From a more practical perspective, Ethereum is an open source, globally decentralized computing infrastructure that executes programs called smart contracts. It uses a blockchain to synchronize and store the system's state changes, along with a cryptocurrency called ether to meter execution resource costs.

## Compared to Bitcoin

Ethereum shares common elements with other blockchains:

- A peer-to-peer network
- A [Byzantine fault-tolerant consensus algorithm](https://en.wikipedia.org/wiki/Byzantine_fault) to sync state updates (PoW at that time)
- Use of cryptographic primitives like digital signatures and hashes
- A digital currency (ether)

Bitcoin's purpose is to be a digital currency. Ethereum's purpose is to be a *world computer* were everyone can build their own dapp powered by ether.

Bitcoin has a very limited scripting language. Ethereum is designed to be a general-purpose programmable blockchain that runs a *virtual machine* capable of executing *any* code. Ethereum's language is *Turing complete*.

## Components of a Blockchain

Components of an open, public blockchain are (usually):

- A P2P network that connects participants and propagates transactions in blocks
- Messages, in the form of transactions, representing state transitions
- A set of consensus rules
- A state machine that processes transactions according to the consensus rules
- A chain of cryptographically secured blocks
- A consensus algorithm that enforces the consensus rules
- A game-theoretically sound incentivaztion scheme (e.g. proof-of-work)
- One or more software implementations of the above (clients)

All or most of these are usually combined in a single software client. In Bitcoin, the reference implementation is developed by the Bitcoin Core team and implemented as the *bitcoind* client. In Ethereum, there isn't a reference implementation but a *reference specification*, which is the [Yellow Paper](https://ethereum.github.io/yellowpaper/paper.pdf) and there are several clients that implement it.

Keep in mind, that today, there are different kinds of blockchains with all different kinds of characteristics.

## The Birth of Ethereum

All great innovations solve real problems, and Ethereum is no exception. Ethereum was conceived at a time where people recognized the possibilities of Bitcoin and wanted to build more complex things, but the constraints of Bitcoin were too big so the only way was to build a new blockchain from scratch.

In 2013, Vitalik Buterin, a young programmer and Bitcoin enthusiast met with Mastercoin, a project that was working on expanding the Bitcoin protocol. He proposed a new approach that allowed flexible and scriptable contracts, the team at Mastercoin were impressed but they dismissed the proposal.

In December 2013, Vitalik started sharing a whitepaper that outlined the idea of Ethereum: a Turing-complete, general-purpose blockchain. A few dozen people saw this early draft and helped Vitalik evolve the proposal. Gavin Wood reached out to Vitalik and became Ethereum’s cofounder, codesigner, and CTO.

In his ['Ethereum Prehistory' post](https://vitalik.eth.limo/general/2017/09/14/prehistory.html), Vitalik mentions Gavin Wood as responsible from changing the vision of Ethereum as a programmable money platform to a general purpose network, part of a 'Web 3' ensemble, along with other 2 pieces called Whisper and Swarm.

Vitalik and Gavin's main idea was to create the general purpose platform on which developers could program any kind of decentralized, secure, censorship-resistant applications without having to worry about the underlying mechanisms of P2P networks, consensus algorithms, etc.

The founders worked for years, building and refining the vision. And on July 30, 2015, the first Ethereum block was mined. The world's computer started serving the world.

## Ethereum’s Four Stages of Development

Ethereum was originally envisioned to have 4 stages of development (this has changed since):

- Frontier
- Homestead
- Metropolis
- Serenity

There were also a few hard forks introduced, some of them:

- Ice Age (Block #200,000): A hard fork to introduce an exponential difficulty increase, to motivate a transition to PoS when ready.
- DAO (Block #1,192,000): A hard fork that reimbursed victims of the hacked DAO contract and caused Ethereum and Ethereum Classic to split into two competing systems.
- Tangerine Whistle (Block #2,463,000): A hard fork to change the gas calculation for certain I/O-heavy operations and to clear the accumulated state from a denial-of-service (DoS) attack that exploited the low gas cost of those operations.

Ethereum was gone through a lot of changes, [this history page](https://ethereum.org/en/history/) is the best place to learn about the changes introduced to Ethereum to date.

## Ethereum: A General-Purpose Blockchain

Ethereum is a distributed state machine, it tracks the state transitions of a general-purpose data store. This means it basically tracks anything that can be expressed in a *key-value tuple*. Ethereum has memory that stores both code and data, and the Ethereum blockchain tracks how this memory changes over time. Like a regular computer, Ethereum can load code into its state machine and run that code, storing the resulting state changes in its blockchain. Two differences with a regular computer however, are that:

- State changes are governed by the consensus rules
- The state is distributed globally

## Ethereum's Components

- P2P Network: Ethereum runs on the *Ethereum main network*, addressable on TCP port 30303, and runs a protocol called ÐΞVp2p.
- Consensu rules: Defined in the Yellow Paper, but you can also check the [Beige Paper](https://github.com/chronaeon/beigepaper), a more accessible version of the former.
- Transactions: Network messages that include (among other things) a sender, recipient, value and data payload.
- State machine: Ethereum state transitions are processed by the *Ethereum Virtual Machine* (EVM). EVM programs are called smart contracts, are written in high-level languages (like Solidity) and compiled to bytecode for execution on the EVM.
- Data structures: Ethereum's state is stored locally on each node as a database (usually Google's LevelDB), which contains the transactions and system state in a serialized hashed data structure called a [Merkle Patricia Tree](https://ethereum.org/en/developers/docs/data-structures-and-encoding/patricia-merkle-trie/).
- Consensus Algorithm: Ethereum used Bitcoin's consensus model, Nakamoto Consensus, however it moved to PoS in recent years.
- Economic Security: At the time of writing, Ethereum used a PoW algorithm called Ethash.
- Clients: Ethereum has several implementations, two of the most prominent are Go-Ethereum (Geth) and Parity.

## Ethereum and Turing Completeness

What does Ethereum being Turing complete mean? Alan Turing defined a system to be Turing complete if it can be used to simulate any Turing machine. Such a system is called a Universal Turing machine (UTM).

Ethereum's ability to execute a stored program, in a state machine (the EVM), while reading and writing data to memory makes it Turing-complete. Ethereum can compute any algorithm that can be computed by any Turing machine, given the limitations of finite memory.

### Turing Completeness is not a Feature

Turing completeness is very easy to achieve. The [simplest Turing-complete state machine](https://www.sciencedirect.com/science/article/pii/S0304397596000771) known, has 4 states and uses 6 symbols, with a state definition that is only 22 instructions long. Sometimes systems are found to be accidentally Turing complete.

### Implications of Turing Completeness

In simple terms, we cannot predict the path of a program without running it. Turing-complete systems can run in 'infinite loops' by accident. In Ethereum, this poses a challenge: every participating node must validate every transaction, running any smart contracts it calls. Whether by accident or on purpose, a smart contract can be created such that it runs forever when a node attempts to validate it. Even if a smart contract doesn't run an infinite loop, there can be a range of nasty, resource-hogging, memory-bloating, CPU-overheating programs that simply waste resources.

How does Ethereum constrain the resources used by a smart contract if it cannot predict resource use in advance?

Ethereum introduces a metering mechanism called *gas*.

As the EVM executes a smart contract, it carefully accounts for every instruction (computation, data access, etc.). Each instruction has a predetermined cost in units of gas. **When a transaction triggers the execution of a smart contract, it must include an amount of gas** that sets the upper limit of what can be consumed running the smart contract. **The EVM will terminate execution if the amount of gas consumed by computation exceeds the gas available in the transaction**. Gas is the mechanism Ethereum uses to allow Turing-complete computation while limiting the resources that any program can consume.

How does one get gas to pay for computation on the Ethereum world computer?

Ether needs to be sent along with a transaction and it needs to be explicitly earmarked for the purchase of gas, along with an acceptable gas price. Gas is purchased for the transaction, the computation is executed, and any unused gas is refunded back to the sender of the transaction.

## From General-Purpose Blockchains to Decentralized Applications (DApps)

Ethereum started as a general-purpose blockchain that could be programmed, but very quickly evolved to become a platform for programming Dapps. DApps represent a broader perspective than smart contracts. A DApp is, at the very least, a smart contract and a web user interface.

In addition, many DApps include other decentralized components, such as:

- A decentralized (P2P) storage protocol and platform
- A decentralized (P2P) messaging protocol and platform

## The Third Age of the Internet

This sections explains why we call it web3.

## Ethereum’s Development Culture

In Ethereum, the community's development culture is focused on the future rather than the past. If a change is needed, it is implemented, even if that means invalidating prior assumptions, breaking compatibility, or forcing clients to update.

As a developer is that you must remain flexible and be prepared to rebuild your infrastructure as some of the underlying assumptions change. **You can’t simply "upgrade" your smart contracts. You must be prepared to deploy new ones, migrate users, apps, and funds, and start over.**

**Note:** Ironically, this also means that the goal of building systems with more autonomy and less centralized control is still not fully realized. Autonomy and decentralization require a bit more stability in the platform than you’re likely to get in Ethereum in the next few years. In order to "evolve" the platform, you have to be ready to scrap and restart your smart contracts, which means you have to retain a certain degree of control over them.


## Why Learn Ethereum?

Blockchains have a very steep learning curve, as they combine multiple disciplines into one domain: programming, information security, cryptography, economics, distributed systems, peer-to-peer networks, etc. Ethereum makes this learning curve a lot less steep. It's easy to write code in Ethereum, but it's very hard to write good and secure code.

