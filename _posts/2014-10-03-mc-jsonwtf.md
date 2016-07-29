---
layout:     post
title:      "Minecraft JSON WTF…"
date:       2014-10-03
categories: tutorial
tags:       ["Minecraft","JSON","rant",]
published:  false
---

In Minecraft most of things can be created via  a command and a JSON dictionary for example a book.

![The Game Theory in Minecraft](https://pbs.twimg.com/media/BzBXPxTIAAAWMIw.jpg "The Game Theory in Minecraft")

## The String

If you want a title in a book for example let's say like in LaTeχ Title then author then date, 
and with magic of JSON you can assign a color or a format like bold or underlined to it:

{% highlight json %}
{
    "text": "",
    "extra": [
        {
            "text": "\n\n\n\n\n      ",
            "color": "reset"
        },
        {
            "text": "The Game Theory",
            "underlined": true,
            "color": "reset",
            "bold": true
        },
        {
            "text": "\n\n      ",
            "color": "reset"
        },
        {
            "text": "Jean Tirole et al.\n",
            "color": "reset",
            "bold": true
        },
        {
            "text": "\n       1991",
            "color": "reset"
        }
    ]
}
{% endhighlight %}
__Note that the json in minecraft is not formated for 'human' reading__

Easy peasy, totally legit JSON, strange tho that you cannot put text in the root text variable without making the game ignore everything…
Let's continue with the book.

## The Book

The book is a dictionary with:

* an _author name_, 
* a _title_ and 
* a _list of pages_

the author & title are used by the game to show information when hoovering the mouse on it.

Each pages shall contain around 464 characters (around because words that are too long at the end of each line are reported to the next one.), if there's too much in the page, the surplus is not shown because it's outside of the page. 

Ok seems easy… **BUT NO ‼**

The author, title and page variable labels **Must Not be quoted**.
AND for the list of pages… a page is a _String_ of JSON formated of previously presented strings with double quotes escaped.

so a book looks like something like that:

{% highlight json %}
{
    title:The Game Theory,
    author:J.Tirole,
    pages:[
        "{
            \"text\": \"\", 
            \"extra\": [{\"text\": \"page 2...\", \"color\": \"reset\"}]
        }", 
        "{
            \"text\": \"\", 
            \"extra\": [{\"text\": \"page 3...\", \"color\": \"reset\"}]
        }"
        ]
}
{% endhighlight %}
__I spend my life in batch & shell scripting, I still new to real coding, but this seems to be inconsistent.__



## The Command

The command to spawn the book is:

{% highlight json %}
/give @p Minecraft:written_book 1 0 {title:The Game Theory,author:J.Tirole,pages:["{\"text\": \"\", \"extra\": [{\"text\": \"\n\n\n\n\n      \", \"color\": \"reset\"}, {\"text\": \"The Game Theory\", \"color\": \"reset\", \"underlined\": true, \"bold\": true}, {\"text\": \"\n\n      \", \"color\": \"reset\"}, {\"text\": \"Jean Tirole et al.\n\", \"color\": \"reset\", \"bold\": true}]}", "{\"text\": \"\", \"extra\": [{\"text\": \"page 2...\", \"color\": \"reset\"}]}", "{\"text\": \"\", \"extra\": [{\"text\": \"page 3...\", \"color\": \"reset\"}]}"]}
{% endhighlight %}


So yeah I don't know, is it a Java dev thing to troll people or what ?

Next time we are going to see how to spawn signs.
␄
