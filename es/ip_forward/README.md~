Podemos activar el ip forward ejecutando como root el comando sysctl:

`>> sudo sysctl -w net.ipv4.ip_forward=1`

Y desactivarlo:

`>> sudo sysctl -w net.ipv4.ip_forward=0`

Esta activación durará mientras no cerremos el sistema y cuando lo volvamos a iniciar el ip_forward estará a cero por defecto. Si queremos hacerlo permanente, no tenemos más que editar el fichero /etc/sysctl.conf y "descomentar" la línea:

```
# net.ipv4.ip_forward=1
```
Dejándola así:

```
net.ipv4.ip_forward=1 
```

Ahora ejecuta en tu máquina:

```
sudo iptables -A FORWARD -j ACCEPT
sudo  iptables -t nat -A POSTROUTING -s 192.168.7.0/24 -o eth0 -j MASQUERADE
```

