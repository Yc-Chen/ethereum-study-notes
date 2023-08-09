## How Ethereum Runs and Upgrades

Ethereum is 'run' by thousands of 'nodes', aka computers or VMs that retrieve state and jointly change the state by executing transactions. Compared to traditional software, its deployment of a new version is 'done' by each node upgrading their client software. This website shows the version distribution and is also tracked by Ethereum core devs: https://ethernodes.org/
> [!NOTE] Ethereum Nodes
> By 2023-04-04, there are ~12000 nodes around the world. See also [[Blockchain Nodes]] for their total node numbers.

> [!NOTE]- Ethereum testing is a joint effort
> Marius (Ethereum code dev) explains Ethereum testing in this video: https://www.youtube.com/watch?v=WpbaWAwtG_M
> Some highlights:
> * Lots and lots of blockchain test for any clients to use
> * If different valid clients validate chains differently, it will end up hardforking
> * Ethereum core devs monitor the versions of clients running there
> 
> See also: https://cointelegraph.com/news/vitalik-reminds-node-operators-to-update-client-before-the-bellatrix-upgrade

> [!NOTE]- Merge Upgrade and Client Version Distribution
> https://cointelegraph.com/news/vitalik-reminds-node-operators-to-update-client-before-the-bellatrix-upgrade
> Quote:
> 73.5% of all node operators were Merge ready, meaning 26.5% of node operators were yet to update their clients.
>  Vitalik reminds people on twitter to upgrade their software. Otherwise they risk syncing to the pre-fork chain.
>  
>  So if majority of node operators are not upgrading to a breaking-change version, it means Ethereum will face a hard fork.


## Ethereum Clients, Beacon Chain, Node

### Consensus Client and Execution Client
A 'Node' is the abstraction of running Ethereum clients(software). You need to run 2 types of clients post-merge: the consensus client and the execution client. For each client, you have multiple choices. The **consensus clients** are agreeing with each other on who determines the block, like 'guiding' the work of **execution client**, and the data it produces are called 'beacon chain', next to the execution chain. A running consensus client is also referred to a beacon node.

Since PoS, the part of the traditional Ethereum client(execution client) to agree which is the canonical(correct) chain is overtaken by consensus client, but the rest is still needs to be handled:

* transactions
* EVM

Therefore the name 'execution': for executing transactions and smart contracts.

Historically, during PoW, Ethereum needed one client, i.e. the 'execution client'. The mining algorithm itself guarantees only one node is able to come up with a good calculation at a time, so there is no need for 'consensus' - multiple nodes agreeing on who determines the block. Later on, moving to PoS, Ethereum community decided to create new clients to manage such consensus for the better modularity design and client diversity.

> [!NOTE]- Why 2 clients? - My Take
> One reason to start a new client is also to adopt new technologies while not to disrupt the existing ecosystem too much. For example, the API between wallets and Ethereum nodes is unchanged during the upgrade; but consensus client uses REST API instead of JSON-RPC.


### Naming Conventions
The namings of consensus clients follow the analogy of 'beacon'. The one that I'm going to study is called **lodestar**, similar to the function of 'beacon'. The protocol upgrade names of consensus client are star names: **Bellatrix**, **Capella**. See more at [consensus-specs](https://github.com/ethereum/consensus-specs/tree/dev/specs). Whereas the protocol upgrade names of execution client are city names: **Paris**, **Shanghai**. See more at [execution-specs](https://github.com/ethereum/execution-specs/tree/master/network-upgrades/mainnet-upgrades).

> [!NOTE]- How Merge Happened
> Beacon nodes have started before the merge. But they become effective only after the merge. There was not accurate merge moment but it is somewhat estimated through 'Terminal Difficulty', which is an ever-increasing number for Ethereum network.

For more information about the separation of 2 clients:  
[https://ethresear.ch/t/eth1-eth2-client-relationship/7248](https://ethresear.ch/t/eth1-eth2-client-relationship/7248)
For an overview of Ethereum clients, visit https://ethereum.org/en/developers/docs/nodes-and-clients/

### Node and Validator
Most cases, a **node** refers to a VM that runs consensus client and execution client. There are some special cases like light node, archive node, etc.

A **validator** participates in Eth staking. **A node can have multiple validators**. I guess most people would only run a node if they can also get reward, which is through staking after the merge.

**miner** is a well-known name that is equivalent of validator but for proof-of-work chains.

### Epoch, Slot and Block
32 Slots = 1 Epoch. 1 slot = 12 seconds.
A block is the content at a specific slot in a specific epoch, like [this one](https://etherscan.io/block/17834475).

### Fork Choice
The name for multiple branches of the chain. After the merge, the branch with the most attestations wins.