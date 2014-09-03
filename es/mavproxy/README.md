# Mavproxy y mavinit.scr
Mavproxy será una herramienta que usaremos para realizar y controlar los logs de vuelo.
[Aquí](http://tridge.github.io/MAVProxy/) estan las instruncciones de descarga.

Algunos modulos que probablemente también sean necesarios:
`sudo apt-get install python-opencv python-wxgtk`
`sudo apt-get install python-wxgtk2.8`
`sudo apt-get install python-matplotlib`
`sudo apt-get install libwxgtk2.8-dev`

También necesitaremos descargar el script `mavinit.scr`que contiene un conjunto de aliases muy útiles en al realización de pruebas de motores. Para descargarla hacemos lo siguiente:
```
wget http/tridge.github.io/MAVProxy/files/mavinit.scr
```

Es recomendable que se guarde en el directorio donde se lanzará Mavproxy, para no tener que añadir rutas.

Por último con el comando `less mavinit.scr`podemos ver lso alias para los gráficos.
