(Alias of [[gossip network]])

The gossipsub is a protocol that took inspiration on how gossip spread among people. It is a whole subject of itself. If you are interested, you can look up by searching terms like 'gossipsub', 'gossip protocol'. As for understanding Ethereum, it's important to know that, while the execution client pretty much had to implement its own p2p protocol, the consensus client relies on the gossipsub to abstracts away the p2p communication. 


> [!NOTE]- Demystifying libp2p Gossipsub
> In this [video](https://www.youtube.com/watch?v=BUc4xta7Mfk) description, "ETH2.0 is evaluating libp2p gossipsub as a decentralized, peer-to-peer publish/subscribe mechanism for validators, proposers and attesters to quickly disseminate data throughout the entire network."

Building on top of gossipsub, what Ethereum has yet to define is what messages to send. The table is from [p2p-interface#topics-and-messages](https://github.com/ethereum/consensus-specs/blob/dev/specs/phase0/p2p-interface.md#topics-and-messages) with only specs of phase-0. But it shows how Ethereum uses gossipsub:

| Name                             | Message Type              |
|----------------------------------|---------------------------|
| `beacon_block`                   | `SignedBeaconBlock`       |
| `beacon_aggregate_and_proof`     | `SignedAggregateAndProof` |
| `beacon_attestation_{subnet_id}` | `Attestation`             |
| `voluntary_exit`                 | `SignedVoluntaryExit`     |
| `proposer_slashing`              | `ProposerSlashing`        |
| `attester_slashing`              | `AttesterSlashing`        |

A gossip client is obliged to give a response as one of: `[Accept]`, `[Reject]` and `[Ignore]`(See also [MessageAcceptance](https://docs.rs/gossipsub/0.27.0/gossipsub/enum.MessageAcceptance.html)). In the lodestar codebase, they are defined as `GossipAction.REJECT` or `GossipAction.IGNORE`. The key difference between `[Ignore]` and `[Reject]` is that, `[Ignore]` will not stop message spreading whereas `[Reject]` will. So usually messages that might be valid for other nodes but not (yet) for this node will have `[Ignore]` response.