---
title: "Minecraft — Bin to BCD converter"
categories: tutorial
tags:   Minecraft, redstone, binary,
date:   2014-10-05T04:14:28
layout: post
published: True
---

**Note：**_This is a copy of my original article[『Minecraft — Bin to BCD converter』](http://ryuutei.wordpress.com/2013/07/10/Minecraft-bin-to-bcd-converter/)on wordpress published the 2013-08-10, with few corrections_

**Version：**_Minecraft beta 1.3+_


Last year I used to build my stupid unfinished broken processor in Minecraft (which I finally downgraded to a weird and big adder (¬\_¬) ), I was working on a bin to BCD converter too. Then I found the awesome [Hans Lemurson’s Binary to BCD converter][hl] (which has decimals digits). For my output I copied the visible “binary input” part and made my own “Add3 part” and output, because it’s impossible to see anything in the video… But it's absolutely not a big deal, the most complex part is to build a compact input and Hans Lemurson made it perfectly. (my Add3 module presented here is certainly the same as him, I don’t see any other way to make it in such a compact building)


![Bin to BCD convertor](https://pbs.twimg.com/media/BzNJnKZCAAAq7nd.jpg)


# Input & “Algorithm” part:

![First（upper）layer of the Binary to BCD converter)](https://pbs.twimg.com/media/BzNJmciCEAExQN_.png "First（upper）layer of the Binary to BCD converter")

The upper layer is the main algorithm, that permanently lit the beneath layer when no input is done. (see why in the “Add 3 layer” part)

The 4 horizontal rows are the binary input, from top to bottom they are the input of the values  `0b0001`, `0b0010`, `0b0100`＆`0b1000`_（this last input is the "eith" which is powered only by a previous Bin to BCD converter）_.
They are easily powered by a torch from above.

For example, the first input row will keep the rows `1`, `3`, `5`, `7`＆`9` powered in the next layer, while the others lines（`2`, `4`, `6`＆`8`）will be off. (⁖ When there is an input, the torches will not provide power to the Add 3 module layer, while the repeaters will)


* * *


# “Add 3 Layer”:

This layer will "shift" the input or more precisely will add 3 to the value if the input is 5 or greater.

![Second（middle）layer of the Binary to BCD converter（don’t pay attention to the redstone dust crossing）](https://pbs.twimg.com/media/BzNJmWzCEAEt0ur.png "Second（middle）layer of the Binary to BCD converter（don’t pay attention to the redstone dust crossing）")

all lines of this layer must be powered when there’s no input. When a line isn’t powered it will light the output (⁖ it’s just a big inverted output.)

From left to right the return values of those columns are: 

* `0b1100`
* `0b1011`
* `0b1010`
* `0b1001`
* `0b1000`（8）
* `0b0100`（4）
* `0b0011`
* `0b0010`
* `0b0001` 

Which are passed to the bottom layer. It's every output combinaison possible for the converter. 

You can see that when you input 5 or more, 3 is added to the stream.

The redstone part is self explanatory.

*N.B.* _torches in this level mustn’t have a bloc above, at the risk of powering a line beside, it’s the blocs where sits the repeaters that will bring problems ; I made the mistake inadvertently twice._ ಠ\_ಠ (stupid mistakes)


* * *


# Output/BCD Line: 

![Third（bottom）layer of the Binary to BCD converter](https://pbs.twimg.com/media/BzNJmUcCYAA8FR9.png "Third（bottom）layer of the Binary to BCD converter")

From top to bottom the lines are the returned values of:
* `0b0001`
* `0b0010`
* `0b0100`
* `0b1000`

This last layer may be  a part of the final binary coded decimal output or, if you want a bigger input, more converters must be concatenated.（cf. [John Loomis’ paper “Binary to BCD Converter”][b2bcd]）

There’s nothing special in this layer.


* * *


# In conclusion，
this is a really smart construction that let you stack a in a neat way many convertors. And the pattern is not too complicated to remember.




# References

* ["Hans Lemurson’s video."][hl]
* ["bin to BCD converter by John Loomis."][b2bcd]
* Real life "BDC"（sort of） [FranLab：Diode Steering For Displays](http://youtu.be/JNbDdnEpAOQ)

[hl]: http://youtu.be/Z-JxYhm3EsI "Hans Lemurson’s video."
[b2bcd]: http://www.johnloomis.org/ece314/notes/devices/binary_to_BCD/bin_to_bcd.html "bin to BCD converter by John Loomis."

␄

