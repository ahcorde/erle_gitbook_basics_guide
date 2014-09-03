# BusTest: Sensors testing


The BusTest is used to check the sensors status.

To execute it do the following:

Let's suppose we are in `/root` (with the command `pwd` you can verify where you are).We get into the `/build` folder by  doing `cd build` and execute the following command line:
```
BusTest.build/BusTest.elf
```

By the moment we should verify that the`MOU9250`y `MPU6000` sensors answer.The code displayed on the screen should be something like:

```
WHO_AM_I for MPU9250: 0x71
WHO_AM_I for LSM9D50: 0xFF
WHO_AM_I for MPU6000: 0x68
```
