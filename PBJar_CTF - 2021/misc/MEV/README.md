# MEV

**Author:** AOx0 :: Alejandro

> The miner of Block #12983883 on the Ethereum Blockchain partakes in the common practice of MEV. What is the exact amount of Ether that was transfered to the miner as a bribe from the transaction that was included first in this block? Info about MEV: https://ethereum.org/en/developers/docs/mev/ Flag format: flag{0.006942069420}



> Maximal (formerly "miner") extractable value (MEV) refers to the maximum value that can be extracted from block production in excess of the standard block reward and gas fees by including, excluding, and changing the order of transactions in a block.

Another video: https://www.youtube.com/watch?v=fBR5Rjwk5C4



After reading the info about MEV we get to know that on a MEV various addresses, incluiding bots, to pay a certain amount of money and gain a little bit extra.

This type of actions very often involve bots programmed to pay ETH to miners (as a bribe) for them to stop competing in the auction. So, the mission is to find the amount of ETH the bot payed.



So, we go to [EtherScan](https://etherscan.io) and look up the block 12983883

![](https://i.imgur.com/IQDsXo7.png)

We click on transactions and navigate to the first one of the block:

![](https://i.imgur.com/VaWF0Q7.png)

![](https://i.imgur.com/WmDYCsG.png)

![](https://i.imgur.com/9J0A8wL.png)

Then we click on its TXN Hash `0xddb777fbc72b8c3f331f...` to view more information.

![](https://i.imgur.com/HjvhUwb.png)

And there we have it. The MVE bot sent to `0xb7...` the amount of `0.009672680170055358`.

**Just for the record:** That information about the transaction was not displayed like that at the moment of the competition. To find that out, you needed to go to `Internal Txns` and analyze the actions.

![](https://i.imgur.com/DiTGF2L.png)

So, the flag is `flag{0.009672680170055358}`