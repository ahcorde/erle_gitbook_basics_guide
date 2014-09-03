# Fligth logs


The fligth logs are stored at `rootfs`.
If we connect the SDcard to our PC and we introduce the command `mount`we can see where has it been mounted. For example at `/media/rootfs`.
Doing :
```
cd /media/rootfs
```
We get located at the `rootfs`partition. The logs get tored at `/var`. Now we want to recover the last log from, for example, `ArduRover`:

```
cd /var/APM
```
Here we find all the `APMrover2` logs and a file called `lastlog.txt`.
```
less lastlog.txt
```
shows us the name of the last log, let's suppose `5.BIN`.
Now we can copy it to the  `Logs` folder at our home, by doing:
```
cp 5.BIN ~/Logs
```

The logs generally are added to https://github.com/erlerobot/drones_logs
