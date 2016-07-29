---
layout:     post
title:      "How to launch Mac OSX Terraria Server v1.3.0.8"
date:       2015-08-18
categories: Coding
tags:       ["game", "shell", "Terraria"]
published:  true
---

Few days ago the First Terraria DRM-Free on  Mac OSX & GNU/Linux was released.

The files of the dedicated server gave by Re-Logic don't start by itself.
But it's easily fixable with few commands in the terminal.

First fews infos〔[source](http://forums.terraria.org/index.php?threads/terraria-1-3-0-8-can-mac-linux-come-out-play.30287/)〕

* Mac OSX:    `~/Library/Application Support/Terraria`
* GNU/Linux:  `~/.local/share/Terraria`, or `$XDG_DATA_HOME/Terraria`


Now in a shell:

{% highlight sh %}
➜  unzip terraria-server-mac-1308.zip
➜  cd Mac/Terraria\ Server.app/Contents/MacOS
➜  chmod 755 TerrariaServer.bin.osx
➜  chmod 755 TerrariaServer
{% endhighlight %}

Edit the `serverconfig.txt` file as your wishes.
〔It is exactly the same file the windows server uses.〕
〘Don't forget to update the paths used by the server〙

And then you can launch the server with the command:

`./TerrariaServer -config serverconfig.txt`


you can also launch the server in a tmux client & then detach it（CTRL-b d）you will then be able to access it in another term or ssh session;
you shall first link or add TerrariaServer to your $PATH variable, 
but you can escape that by moving the server files to the Terraria save folder and using this command:

{% highlight sh %}
tmux new-session -s Terraserver "~/Library/Application\ Support/Terraria/server/Terraria\ Server.app/Contents/MacOS/TerrariaServer -config ~/Library/Application\ Support/Terraria/server/Terraria\ Server.app/Contents/MacOS/serverconfig.txt"
{% endhighlight %}


or a screen (inferior but still do the work and quickier to learn) and then detach it too.（CTRL-a d）
`screen "./TerrariaServer -config serverconfig.txt"`

I didn't try to launch it with the icon, it's not interesting to keep a server in a window you can't close.

Enjoy.␄
