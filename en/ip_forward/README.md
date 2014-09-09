As with any sysctl kernel parameters we can change the value of `net.ipv4.ip_forward` on the fly **(without rebooting the system)**:

`>> sudo sysctl -w net.ipv4.ip_forward=1`

or disable:

`>> sudo sysctl -w net.ipv4.ip_forward=0`

This way is going to work while you don't reboot your system. When you turn on your computer `ip_foward` will be disabled. If we want to make this permanent, you need to edit the file `/etc/sysctl.conf` and uncomment the line:

```
# net.ipv4.ip_forward=1
```
In this way:

```
net.ipv4.ip_forward=1
```
Now you have to execute in your machine

```
sudo iptables -A FORWARD -j ACCEPT
sudo  iptables -t nat -A POSTROUTING -s 192.168.7.0/24 -o eth0 -j MASQUERADE
```

