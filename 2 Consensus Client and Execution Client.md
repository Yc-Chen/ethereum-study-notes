---
---

> To participate as a validator, a user must deposit 32 ETH into the deposit contract and run three separate pieces of software: an execution client, a consensus client with validator(s) imported.
https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/#validators

It mentions that you need:
- consensus client and
- execution client

to run an Ethereum node.

Therefore I chose one codebase for each client and I ended up with:

| client | name | version |
| --- | --- | --- |
| Execution client | geth | v1.11.2 |
| Consensus client | lodestar | v1.5.1 |

'geth' is the most famous and oldest(?) Ethereum client, so there are be plenty documentations and QAs online. 'lodestar' is one of the consensus client, and I chose it mainly because I'm more familiar with the language JavaScript.