# Mavproxy and mavinit.scr


Mavproxy is a toool we will use to analize and controll the fligth logs
[Here](http://tridge.github.io/MAVProxy/) you canf ind the download isntructions.

Some odules will be, probably, necessary.
`sudo apt-get install python-opencv python-wxgtk`
`sudo apt-get install python-wxgtk2.8`
`sudo apt-get install python-matplotlib`
`sudo apt-get install libwxgtk2.8-dev`

Also, we need to download the  `mavinit.scr` scipt, that contains some aliases, very useful when doing motors tests.For downloading it , do the following:
```
wget http://tridge.github.io/MAVProxy/files/mavinit.scr
```

It is very recommendable to store it in the directory where you will launch Mavproxy, for not need to add a route.

Lastly, with the `less mavinit.scr` command, you can see the different aliases for the graphs.
