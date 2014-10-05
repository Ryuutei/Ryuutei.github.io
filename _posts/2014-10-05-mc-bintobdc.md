---
title: "Minecraft — Bin to BDC converter"
categories: Hardware
tags:   Minecraft, redstone, binary,
date:   2014-10-05T04:14:28
layout: post
published: True
---

__This is a copy of my original article[『Minecraft — Bin to BDC converter』](http://ryuutei.wordpress.com/2013/07/10/Minecraft-bin-to-bcd-converter/)on wordpress published the 2013-08-10, with few corrections__

![Minecraft](http://ryuutei.files.wordpress.com/2013/07/Minecraft.png "Minecraft icon")

Last year I used to build my stupid unfinished broken processor  in Minecraft (which I finally downgraded to a weird and big adder :D), I was working on a bin to BCD converter too. Then I found the awesome [Hans Lemurson’s Binary to BCD converter][hl] (who has decimals digits). For my output I copied the visible “bin input to selection rows” and made my own “selection part” and output. Because it’s impossible to see anything in the video… Anyway the most interesting and complex part was done by Hans Lemurson and it’s visible in the video. (my selector is certainly the same as him, because I don’t see any other way to make it in such a compact building.)


![Bin to BDC convertor](http://ryuutei.files.wordpress.com/2013/07/b2bcd.jpg)


# Input & “Algorithm” part:

![First（upper）layer of the Binary to BCD converter)](http://ryuutei.files.wordpress.com/2013/07/3.png?w=300&h=225 "First（upper）layer of the Binary to BCD converter")

The upper layer is the main algorithm, that will permanently light the beneath layer when no input is done. (see why in the “selector” part)

The 4 horizontal rows are the binary input. They are easily powered by a torch from above. From up to bottom they are the input of  `0b0001`, `0b0010`, `0b0100`＆`0b1000` .

For example, the first input row will keep the selector rows 2, 4, 6 and 8 powered while the other will be shutdown. (ie. When there is an input, the torchs will not provide power to the selector layer, while the repeaters will.)



# ”Selector” part:

![Second（middle）layer of the Binary to BCD converter（don’t pay attention to the redstone dust crossing）](http://ryuutei.files.wordpress.com/2013/07/2.png?w=300&h=225 "Second（middle）layer of the Binary to BCD converter（don’t pay attention to the redstone dust crossing）")

all lines of this layer must be powered when there’s no input. When a line isn’t powered it will light the output (ie. it’s just a big inverted output.)

From left to right the values of those columns are: `1001`, `1000`, `111`, `110` `101`, `100`, `11`, `10`, `1`. This part is pretty easy to understand and it’s self explanatory.

*N.B.* _torches in this level mustn’t have a bloc above, at the risk of powering a line beside, it’s the blocs where sits the repeaters that will bring problems ; I made the mistake inadvertently twice._ ಠ\_ಠ (stupid mistakes)


# Output/BCD Line: 

![Third（bottom）layer of the Binary to BCD converter](http://ryuutei.files.wordpress.com/2013/07/1.png?w=300&h=225 "Third（bottom）layer of the Binary to BCD converter")

This last layer may be the final binary coded decimal output or, if you want bigger input, another converter but everything about this is really well explained in the [John Loomis’ paper “Binary to BCD Converter”][b2bdc].

There’s nothing special in this layer that need an explanation.



# In conclusion，
this is a really smart construction that let you stack a in a neat way many convertors. And the pattern is not too complicated to remember.




# References

* ["Hans Lemurson’s video."][hl]
* ["bin to BCD converter by John Loomis."][b2bdc]

[hl]: http://youtu.be/Z-JxYhm3EsI "Hans Lemurson’s video."
[b2bdc]: http://www.johnloomis.org/ece314/notes/devices/binary_to_BCD/bin_to_bcd.html "bin to BCD converter by John Loomis."

␄

