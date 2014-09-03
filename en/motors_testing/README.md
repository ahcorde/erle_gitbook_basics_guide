# Motors testing


> Read before the "Mavproxy y mavinit.scr"

First we connect with erle-board:
```
ssh root@192.168.7.2
```
Next we need to have compiled the code we are going to run, suppose `ArduCopter`; if not:
```
cd adupilot/ArduCopter
make clean;make pxf
```
Checks the overlays:
```
cat $SLOTS
```
We need to verify that `BB_BONE_PRU`  comes always before `BB_SPI#-SWP`.

Check the kernell (56 or later):
````
uname -a
```
Last thing to do, is launching a socket and wait for someone to connect(in this case the machine itselfs, since there is not RC transmitter for now):
(Note: For running this command line like this, get located at `/root`).
```
build/ArduCopter.build-MPU9250/ArduCopter.elf -A tcp:*:6000:wait
```
For `ArduRover`:
```
build/APMrover2.build/APMrover2.elf -A tcp:*:6000:wait
```
For `ArduPlane`:
```
build/ArduPlane.build/ArduPlane.elf -A tcp:*:6000:wait
```


Now we open a Linux terminal window. We should have [Mavproxy](http://tridge.github.io/MAVProxy/) and its complements installed; in addition to `mavinit.scr`.In case, everything is all rigth we connect to the port waiting by:
```
mavproxy.py --master tcp:192.168.7.2:6000
```
We will ge the prompt `Ready to fly`

If we write:`script mavinit.scr` the aliases get charget, so we can analize garph in real time in a simply way.
- grc : channels
- gthr: throttle
- gservo: servo outputs
-  `less mavinit.scr` for more aliases

*Note:*In  `ArduCopter` case remember to change  `param set ARMING_CHECK 0`.

Lastly launch the command `arm throttle` and start turning the values:
- `rc all 1300`(all channels)
- `rc 3 1450`(channel 3)
- ...


Link to a video-tutorial step-by-step:https://www.youtube.com/watch?v=Mv6k5hP2yuc&feature=youtu.be
