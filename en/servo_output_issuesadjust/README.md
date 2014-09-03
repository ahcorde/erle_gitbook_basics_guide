# Servo output issues:Adjust
In case that the value of the servo-output is always zero, the following adjust must be done:

At `/root`, do `cd ..` y `ls`;between other we will see a folder named  `lib`:
```
cd lib/firmware
```
Inside the folder we do:
```
rm pwmpru1
```
```
rm rcinpru0
```
to erase this files.

Now we get back to `/root` doing `cd ~`:
```
cd ardupilot/Tools/Linux_HAL_Essentials
```
Inside this directory we execute
```
source startup.sh load
```
Then reboot with the command:`reboot`.

Now check again the motors testing and see if `gservo` offers different values.
