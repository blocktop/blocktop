# blocktop

> Blocktop is a library of blockchain components created for architects and developers. It is designed to allow components to easily be swapped out to promote experimentation and optimization.

## Table of Contents

- [Overview](#overview)
- [Components](#components)
- [Demo](#demo)
- [Maintainers](#maintainers)
- [License](#license)

## Overview

Blocktop is a library of blockchain components created for architects and developers. It is designed to allow components to easily be swapped out to promote experimentation and optimization. 

In this manner, blocks may carry transactions of any type, and those transactions may write any type of state into the globally synchronized ledger. New transactions and new types of state may be registered to expand the system.

#### Deep Consensus
 
The heart of the system. It manages incoming blocks, confirms blocks, and proposes the best head blocks from which the blockchain should generate the next block. It is "deep" because it allows for use cases in which winning blocks may enter the system up to a configurable lag time - perfect for systems in which network speed and compute power should not be factors in the consensus process.

#### Block Generator

The interchangeable component that generates new blocks. Proof-of-Work systems can implement their algorithms here, but also swap for lighter-weight algorithms for testing purposes. Similarly Proof-of-Stake systems can create more efficient testing scenarios.

Blocktop has invented an new experimental proof mechanism called **Proof-of-Luck**. Determining which node has the privilege of writing the next block is accomplished through a simple and elegant algorithm that guarantees a single random node without requiring computational power or staking amounts of coin.

#### IPFS-Based Storage

IPFS is a globally-accessible, immutable, content-addressable storage system. Blocktop provides out-of-the box storage in the IPFS MerkleDAG. This allows nodes to review the entire immutable blockchain without having to individually recompute it before participating in block generation and consensus.

#### RPC API

Blocktop exposes internal state to programs such as command line tools, web UIs, and wallets via a simple HTTP RPC mechanism. This mechanism is extensible so that developers can include their own methods in the API.

#### Dashboard

Blockchain metrics and a unique consensus visualization tool are included in a dashboard UI component.

## Components

* [go-spec](https://github.com/blocktop/go-spec) - the interface specifications for all components
* [go-consensus](https://github.com/blocktop/go-consensus) - the deep consensus component
* [go-blockchain](https://github.com/blocktop/go-blockchain) - the blockchain management component
* [go-network-libp2p](https://github.com/blocktop/go-network-libp2p) - the networking component based on [libp2p](https://libp2p.io/)
* [go-store-ipfs](https://github.com/blocktop/go-store-ipfs) - the blockchain state and storage module based on [IPFS](https://ipfs.io/)
* [go-rpc-client](https://github.com/blocktop/go-rpc-client) and [go-rpc-server](https://github.com/blocktop/go-rpc-server) - RPC API client and server
* [go-dashboard](https://github.com/blocktop/go-dashboard) - the visualization UI component

## Demo

Lucky is the demonstration blockchain for blocktop. It uses the Proof-of-Luck consensus algorithm and the IPFS storage module.

Clone the [go-lucky](https://github.com/blocktop/go-lucky) repo.
```
git clone https://github.com/blocktop/go-lucky.git
```

Get [glide](https://glide.sh/).
```
curl https://glide.sh/get | sh
```

Get dependencies.
```
cd go-lucky
glide install
```

Init and run your node. Your node will be connected into the Lucky testnet with several other nodes running around the world (some of which are operated by [blocktop.solutions](http://blocktop.solutions), our commercial arm).
```
lucky init && lucky blockchain
```

Visualize. Run the following and then open a browser to [http://localhost:3000](http://localhost:3000).
```
lucky dashboard
```

## Maintainers

[@strobus](https://github.com/strobus)

## Contributors

Would you like to help out with blocktop development? Fork any repo and submit a pull request!

## License

GPL © 2018 J. Strobus White
Commercial terms available, please [contact me](mailto:strobus@blocktop.io?subject=blocktop license).
