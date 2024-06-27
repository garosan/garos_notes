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

