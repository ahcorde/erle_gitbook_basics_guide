# Cross-compilation 

We can compile the code directly on the board (but it will take a long time to compile) or we try cross-compiling reducing the compile time. 

This will require `gcc-4.7-arm-linux-gnueabihf` and `g++-4.7-arm-linux-gnueabihf`. 

```
>>sudo apt-get install gcc-4.7-arm-linux-gnueabihf g++-4.7-arm-linux-gnueabihf
```

If your system don't find the packets, it's possible to add the repository

In Debian you need to add the repository `deb http://www.emdebian.org/debian/`. 

```
>> sudo gedit  /etc/apt/sources.list
```

Add the next line to the end of the file and save the changes

``` 
deb http://www.emdebian.org/debian/ unstable main
```

Remember to update before try again (sudo apt-get update).

Once we have the packets installed. Go to the directory  `ardupilot/libraries/AP_Compass/examples/AP_Compass_test` and execute:

`>>make pxf`

The compile file is located in `/tmp/AP_Compass_test.build/` with extension `.elf`.

Now we can copy the file in the board (for example in the $HOME), executing:

```
scp /tmp/AP_Compass_test.build/AP_Compass_test.elf root@192.168.7.2:~/
```
