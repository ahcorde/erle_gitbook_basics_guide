# Updating the kernell

Nowadays the available kernell are stored at [this repository](https://github.com/erlerobot/kernels).

Let's supose that we want to update our kernell to the las version stored in [/3.8.13.x/PREEMPT](https://github.com/erlerobot/kernels/tree/master/bbb/3.8.13.x/PREEMPT).

First we download all the files in the folder.
Then we introduce the SDcard (with the image copied, see previous section) on the Linux card reader.

With the command `mount`we can see where  tanto `BEAGLE_BONE` and `rootfs` are mounted.Let's suppose they get mounted in `/media`.

Located at `PREEMPT` directory, we do:
```
cp 3.8.13.23-bone56-ext0.1.zImage /media/BEAGLE_BONE/zImage
```
Then:
```
sudo tar xfv 3.8.13.23-bone56-ext0.1-modules.tar.gz /media/rootfs
```
And last:
```
sync
```

Y ya estaría lista para conectarla a erle-board.
Una vez conectado a erle-board, haciendo `uname -a `deberíamos ver el nuevo kernel.
