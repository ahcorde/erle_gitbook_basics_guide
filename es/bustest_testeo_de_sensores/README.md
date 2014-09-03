# BusTest: Testeo de sensores

El BusTest se utiliza para testear el estado de lso sensores.

Para ejectutarlo se hace lo siguiente:

Supongamos que estamos en `/root` (con el comando `pwd` puedes verificar donde estas).Nos situamos en la carpeta build, haciendo `cd build` y ejecutamos la siguiente línea:
```
BusTest.build/BusTest.elf
```

Por el momento debemos verificar que responden los sensores:`MOU9250`y `MPU6000`.El codigo que obtenemos será algo como:

```
WHO_AM_I for MPU9250: 0x71
WHO_AM_I for LSM9D50: 0xFF
WHO_AM_I for MPU6000: 0x68
```
