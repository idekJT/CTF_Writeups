# tippy tappies

**Author:** AOx0 :: Alejandro

> how'd you get this in the first place :eyes: dids you has logger on me?

The attached file, `tippytappies.pcapng`, has extension `pcapng` which is a PCAP Next Generation Capture File Format that we can open with *Wireshark*.



![](https://i.imgur.com/527aNbc.png)



I was messing around, understanting the structure of the packages, when I found this:

![](https://i.imgur.com/OTiCXBC.png)

That package information plus the description of the challenge and the Protocol of the packages made it  very clear that this is a file of someone's keyboard actions. 



So I decided to add `Keys` as a column.

![](https://i.imgur.com/QRQ29rr.png)

There were lots of packages that do not contain any pressed-key information. Like all  `host -> 2.9.1`. This made everything pretty difficult to analyze.

Thus, I filtered the packages so I could only see the ones that did contain information.  

![](https://i.imgur.com/jkLPEZx.png)

Then I just reviewed every single remaining package, looking for what key was registered. This was faster than you may think lol, I just spammed the `down-key` arrow.

![](https://i.imgur.com/PcNxCis.png)

Example:

| #    | Keys     |
| ---- | -------- |
| 1    | ENTER    |
| 2    | s        |
| 3    | u        |
| 4    | d        |
| 5    | o        |
| 6    | SPACEBAR |
| 7    | a        |
| 8    | ap       |
| 9    | p        |
| 10   | t        |
| ...  | ...      |

So, he updated the repositories, installed weechat, connected to an irc channel and then sent a message to some guy with the flag.

