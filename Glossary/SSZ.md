I'm going to skip the cryptography background here and focus on what it means in code. For deeper dive into cryptography, see links below. 

SSZ is for simple serialize. Its advantage is that it allows you to read a specific part of the data without deserializing the whole object, on the premise that you know the data structure upfront. Therefore in code (based on [[repositories/lodestar/packages/beacon-node/src/chain/blocks/utils/chainSegment.ts]]):
```TypeScript
if (
  !ssz.Root.equals(
	block.message.root,
	child.message.parentRoot
  )
) {
  // ...
}
```

where `ssz.Root.equals` directly compares the `Root` values of the serialized objects. The pseudo code below archives the same thing but takes more computation:
```TypeScript
if (
  ssz.deserialize(block.message.root).Root 
  !== ssz.deserialize(child.message.parentRoot).Root
) {
  // ...
}
```


> [!NOTE]- For more information
> Ethereum Official Documentation: https://ethereum.org/en/developers/docs/data-structures-and-encoding/ssz/
> Eth2book(more recommended): https://eth2book.info/capella/part2/building_blocks/ssz/