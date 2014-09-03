# Testeo de Motores


> Leer antes la sección "Mavproxy y mavinit.scr"

Primero conectamos con erle-board:
```
ssh root@192.168.7.2
```
A continuación debemos terner compilado el codigo que vamos a correr, supongamos `ArduCopter`.
Si no lo tenemos:
```
cd adupilot/ArduCopter
make clean;make pxf
```
A continuación comprobamos los overlays:
```
cat $SLOTS
```
Lo que debemos verificar es que `BB_BONE_PRU` siempre va antes que `BB_SPI#-SWP`.

Chequeamos el kernel(56 o superior):
````
uname -a
```
Y por último lanzamos un socket y esperamos a que alguien (en este caso la propia máquina) se conecte:
(Nota: Para correr este comando tal cual, debemos posicionarnos en `/root`).
```
build/ArduCopter.build-MPU9250/ArduCopter.elf -A tcp:*:6000:wait
```
Para `ArduRover`:
```
build/APMrover2.build/APMrover2.elf -A tcp:*:6000:wait
```
Para `ArduPlane`:
```
build/ArduPlane.build/ArduPlane.elf -A tcp:*:6000:wait
```


Ahora abrimos un terminal en Linux.Deberíamos tener instalado [Mavproxy](http://tridge.github.io/MAVProxy/) y sus complementos más usuales; además de `mavinit.scr`.En caso de que este todo listo introducimos el siguiente comando (nos conectmos al puerto en espera):
```
mavproxy.py --master tcp:192.168.7.2:6000
```
Nos aparecerá el prompt de `Ready to fly`

Si escribimos:`script mavinit.scr` se cargan los aliases y de forma sencilla podemos analizar gráficos en tiempo real, por ejemplo:
- grc : canales
- gthr: throttle
- gservo: servo outputs
-  `less mavinit.scr` para ver más

*Nota:*En caso de `ArduCopter` recuerda hacer `param set ARMING_CHECK 0`.

Por último utiliza el comand `arm throttle` y comienza a variar los valores:
- `rc all 1300`(todos los canales)
- `rc 3 1450`(un canal)
- ...


Link a un video tutorial paso a paso:https://www.youtube.com/watch?v=Mv6k5hP2yuc&feature=youtu.be
