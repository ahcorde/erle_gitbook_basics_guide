# Download/update/compile ardupilot



#####Download ardupilot

You shoud download ardupilot form the GitHub repository: [/Beaglepilot/ardupilot](https://github.com/BeaglePilot/ardupilot).

With the following command you get the local repository:

````
git clone https://github.com/BeaglePilot/ardupilot.git
```

#####Compile ardupilot

Let's suppose we want to compile `ArduCopter` in Linux:

```
cd ardupilot/ArduCopter

make clean;make linux
```
Probably the machine will indicate us that a  `make configure` is missing. We introduce that command and execute `make linux` another time.

In the case we ant to compile `ArduCopter` in the PXF, the same, more or less, must be done:

```
cd ardupilot/ArduCopter

make clean;make pxf

```

#####Update ardupilot

Now we ant to update the ardupilot version of our erle-board:
- Download the current ardupilot repository
- Check that the last commint coincides with the one of the remote repository by using `git log`.
-  Also we can check that it compiles.
-  Erase the `ardupilot` folder forom the board:
```
rm -r ardupilot/
```
-  Copy the new repository to the board:
```
  scp -r ardupilot/ root@192.168.7.2:/root
 ```

####NOTE

Nowadays we are, also, checking the code in: https://github.com/tridge/ardupilot/tree/BBB-WIP

Do:
```
git clone https://github.com/tridge/ardupilot
cd ardupilot
git checkout BBB-WIP
```
We get the code, taht can be passed to the SDcard using `scp`like indicated above.
