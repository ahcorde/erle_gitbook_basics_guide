# Logs de vuelo

Los logs de vuelo se almacenan en `rootfs`.
Si conectamos la tarjeta SD en el lector de tarjetas de nuestro PC y introducimos el comando `mount`podemos ver donde se ha montado; supongamos que en `/media/rootfs`
.
Haciendo :
```
cd /media/rootfs
```
nos colocamoes en la partición. Los logs quedan almacenados en `/var`. Supongamos que lo que queremos es recuperar el último log de `ArduRover`:

```
cd /var/APM
```
Aquí encontramos todos los logs de `APMrover2` y un archivo que se llama `lastlog.txt`.
```
less lastlog.txt
```
nos muestar el nombre del último log, supongamos `5.BIN`.
Ya podemos copiarlo, por ejemplo, a la carpeta `Logs`de nuestro home, haciendo:
```
cp 5.BIN ~/Logs
```

Los logs generalmente se añaden a https://github.com/erlerobot/drones_logs
