# Ethereum Study Notes

## Why
A lot of the articles trying to explain how Ethereum works often make me more confused when I want to understand the whole picture or to dive deeper. The reasons for that are 
- the use of analogies. Analogies are great in explaining one aspect but can put you in the wrong foot for another, e.g. EVM is like a computer on chain but is it really a computer?
- the namings. The namings of various concepts are another source of confusion since many names overlap in their meanings but not exactly the same; in some cases it's totally correct to use them interchangeably and in some cases not, like '[[Deneb]]', an upgrade name of the Ethereum consensus protocol, and '[[EIP-4844]]', an Ethereum protocol proposal that's going to be implemented in the 'Deneb' upgrade.
- the various online articles/QAs published at different stage, especially before and after merge. Before the merge, running one execution client would be enough; after the merge, the execution client must be paired with a consensus client. But lots of outdated articles are still lying around.

Therefore I decided to:
- write a note without any analogies but link the concepts directly to code or specs
- and explain the motivations of names in their first appearance.

This study note is for people with certain technical background. For myself, I'm familiar with concepts like HTTP request and network and I'm comfortable with reading code in general. I'm also familiar with high-level concepts of Ethereum, e.g. from PoW to PoS. So It's probably the best if you have similar background to read my notes.

This study note does **not** dive deep into cryptography and the protocol design. Although they are important, it's still too difficult for me. But hope this note provides a full grasp of Ethereum that makes it easier to do deep dive on specific topics later. 

This study note is based on:

| client | name | version |
| --- | --- | --- |
| Execution client | geth | v1.11.2 |
| Consensus client | lodestar | v1.5.1 |
They are included as submodules under 'repositories' for easier referencing.

In the code it is between the '[[shapella]]' upgrade and '[[Deneb]]' upgrade. In practice, the mainnet upgrade is taken extremely carefully with extra time of testing, so it is before the mainnet 'shapella' upgrade and maybe misses some final fixes.

## Obsidian and VSCode
This note is best viewed with [obsidian](https://obsidian.md/), where you can have the linked articles on hover and you can view the canvas-typed notes like [[5.1 User Submits A Transaction.canvas|5.1 User Submits A Transaction]]. But for code files you need a code editor like VSCode because obsidian does not show them.

## ChatGPT
ChatGPT helped me a lot to understand how Ethereum works. Knowing that its answer may not be accurate, I always explicitly quote ChatGPT. (Am I better than ChatGPT? Dunno.)

## Chapters
Chapters are ordered, except for this README, which unfortunately appears in the bottom of other chapters. To get started, the first chapter is [[1 Ethereum and Its Namings]] and the rest is in order.

## Code
When I include code snippet, I added my own comments by `/* ... */` or skipped part of the code by `// ...`.