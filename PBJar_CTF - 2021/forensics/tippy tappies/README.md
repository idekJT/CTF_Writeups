# tippy tappies

**Author:** AOx0 :: Alejandro



The file `tippytappies.pcapng` has extension `pcapng` which is a PCAP Next Generation Capture File Format that we can open with *Wireshark*.



![](https://i.imgur.com/527aNbc.png)



I messed around understanting the structure of the packages when I found this:

![](https://i.imgur.com/OTiCXBC.png)

That package information make very clear that this is a file capturing some keyboard's actions. I decided to add `Keys` as a column.

![](https://i.imgur.com/QRQ29rr.png)

There are lots of packages, the ones from `host -> 2.9.1` that do not contain any pressed keys information. So i filtered so I can only see packages that do contain information.  

![](https://i.imgur.com/jkLPEZx.png)

Then I just reviewed every single remaining package looking for what key the user pressed. This was faster than you may think lol, just spam the `down-key`.

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

So, he updated the repositories, installed weechat, connected to a channel and then sent a message to someguy with the flag.

