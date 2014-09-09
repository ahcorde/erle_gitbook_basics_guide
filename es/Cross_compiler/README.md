# Compilación cruzada

Podemos compilar el código directamente en la placa (pero tardará tiempo en compilarse) o realizar el cross-compiling reduciendo el tiempo de compilación.

Para ello será necesario tener instalado `gcc-4.7-arm-linux-gnueabihf` y `g++-4.7-arm-linux-gnueabihf`. 

```
>>sudo apt-get install gcc-4.7-arm-linux-gnueabihf g++-4.7-arm-linux-gnueabihf
```

Si no encuentra los paquetes es posible que tengamos que añadir el repositorio.

En Debian se añade el repositorio `deb http://www.emdebian.org/debian/`. 

```
>> sudo gedit  /etc/apt/sources.list
```

Añade al final del archivo y guarda los cambios:

``` 
deb http://www.emdebian.org/debian/ unstable main
```

Recuerda actualizar primero antes de volver a intentarlo (sudo apt-get update).

Una vez tengamos los paquetes instalados vamos al directorio `ardupilot/libraries/AP_Compass/examples/AP_Compass_test` y ejecutamos:

`>>make pxf`

El archivo compilado se encuentra en `/tmp/AP_Compass_test.build/` y tiene extensión `.elf`.

Una vez compilado lo copiamos a la placa (en el $HOME), ejecutando:

```
scp /tmp/AP_Compass_test.build/AP_Compass_test.elf root@192.168.7.2:~/
```
