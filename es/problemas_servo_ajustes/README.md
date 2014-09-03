# Problemas servo: Ajustes

En caso de que el valor de la output de los servos sea siempre cero, se debe realizar el siguiente ajuste:

Estando en el `/root`, hacemos `cd ..` y `ls`debería aparecernos, entre otras, una carpeta llamada `lib`:
```
cd lib/firmware
```
Dentro de esta carpeta hacemos:
```
rm pwmpru1
```
```
rm rcinpru0
```
para borrar esso dos achivos.

Ahora volvemos al home `/root` haciendo `cd ~`:
```
cd ardupilot/Tools/Linux_HAL_Essentials
```
Y dentro de este directorio ejecutamos:
```
source startup.sh load
```
Después de estoreiniciamos, con el comando `reboot`.

Ahora toca probar de nuevo a hacer el testeo de motores y ver si `gservo`ofrece valores diferentes.
