# Actualizar el Kernell

Actualmente los kernells disponibles estan en [este repositorio](https://github.com/erlerobot/kernels).

Supongamos que queremos actualizar nuestro kernel a la última versión, contenida en la carpeta [/3.8.13.x/PREEMPT](https://github.com/erlerobot/kernels/tree/master/bbb/3.8.13.x/PREEMPT).

primero descargamos todos los archivos de la carpeta.
A continuación introducimos la SDcard (con la imagen ya copiada)en el lector de tarjetas y en Linux.

Con el comando `mount`podemos ver donde se montan tanto `BEAGLE_BONE` como `rootfs`.Supongamos que ambas se montan en `/media`.

Situados en el directorio `PREEMPT`, hacemos:
```
cp 3.8.13.23-bone56-ext0.1.zImage /media/BEAGLE_BONE/zImage
```
Luego:
```
sudo tar xfv 3.8.13.23-bone56-ext0.1-modules.tar.gz /media/rootfs
```
Y por último:
```
sync
```

Y ya estaría lista para conectarla a erle-board.
Una vez conectado a erle-board, haciendo `uname -a `deberíamos ver el nuevo kernel.
