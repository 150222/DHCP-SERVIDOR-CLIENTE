## informacion de las caracteristicas.
Vamos a mostrar lso pasos para configurar un servidor dhcp
con las subred `20.20.20.0` la mascara `/27` y el rando de la `10` a la `15`.

### 1º Instalacion.
 Iniciar cuentra terminal y hacer el siguiente comando:
 
```
sudo apt upgrade
```
Apto seguido darle a la S y enter, eso hace que todos los comandos se actualicen a la ultima versión.

---

Instalamos el dhcp server con:
```
sudo apt-get install isc-dhcp-server
```

## 2º Configuracion. 
 A continuacion haremos el siguiente comando  para instalar un servidor dhcp en ubuntu.
```
sudo nano /etc/dhcp/dhcpd.conf
```
Despues añadiras las siguientes cosas.

```
subnet 20.20.20.0 netmask 255.255.255.224 {
    range 20.20.20.10 20.20.20.15;
    option routers 20.20.20.1;
    option domain-name-servers 8.8.8.8, 8.8.4.4;
    option domain-name "exmaple.com";
}

```


Despues de estos comandos cerraremos y guardaremso la carpera con `ctrl s` y luego `ctrl x` 


Despues de configurar el server lo reiniciamos, lo puedes hacer con el siguiente comando:

```
sudo systemctl restart isc-dhcp-server

```
## 3ºConfiguracion del cliente.
Lo primero es descargar `isc-dhcp-client`

```
sudo apt-get install isc-dhcp-client

```

Ahora se pondra el siguiente comando `ip a`, para ver tu ip actual. 

Ahora se quitara tu ip actual con el siguiente comando.

```
sudo dhclient -r
```
Y para asignar uan nueva sera con este comando.

```
sudo dhclient

```

Ahora comprobarecos que la ip de ahora no concuerda con la que nos dio el comando `ip a` y ahora estaremos dentro del rango que queremos.

