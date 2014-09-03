# Copiar una imagen a SDcard

#####Linux

En este [link](https://github.com/erlerobot/wiki/wiki/Copy-image-to-microSD-card) podeis encontrar instrucciones para quemar la imagen usando Linux.

 Asumiendo que la imagen se llame   `erlerobot-ubuntu.img.gz`, y la SDcard se monte en ` /dev/sdb` , escribe en el terminal:
```
zcat erlerobot-ubuntu.img.gz | sudo dd of=/dev/sdb bs=8M
```
Para asegurarse de que la imagen se a copiado, introduce en el terminal:
```
sync
```
#####Mac

En este sistema operativo, deben seguirse los pasos de la imagen:

![sDcard](../erleimg/SDcard2.jpg)

El proceso tardará unos 20-30 minutos.


Después de quemar la imagen en la tarjeta (en cualquiera de los dos SO) comprueba que en Linux se montan tanto `BEAGLE_PILOT` como `rootfs`.Esto puede hacerse usando el comando `mount`.
