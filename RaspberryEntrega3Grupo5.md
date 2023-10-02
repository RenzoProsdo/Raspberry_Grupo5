# Informe Grupo 5
## TP DHCP
## Alumnos: Miller Derek, Prosdocimo Renzo, Tempesti Mateo, Weigandt Timoteo
Tercer Trabajo:  
Se retiran los materiales del armario, se conectan los perisfericos (teclado, mouse y monitor) a la Raspberry, tambien se conecta a un tomacorriente por medio de un cable con punta micro USB y a al switch mediante el cable LAN.

**LOS SIGUIENTES COMANDOS FUERON EJECUTADOS EN LA RASPBERRY**

Para comenzar con la consigna se instalar el servidor DHCP, para instalarlo, se utilizo el siguiente comando:
```bash
$ sudo apt-get install isc-dhcp-server
```
Una vez instalado DHCP, se deben cambiar ciertos parametros dentro de los archivos de configuracion de dhcp. Para lograr esto se ejecuta el siguiente comando, el cual abre un editor de texto en la terminal, con el cual podremos cambiar los parametros necesarios:
```bash
$ sudo nano /etc/network/interfaces
```
Al ingresar a este archivo deberemos remplazar todos los archivos existentes por las siguientes lineas:
```bash
auto eth0
iface eth0 inet static
address 192.168.5.2
netmask 255.255.255.0
gateway 192.168.5.1
```
Las ips son a eleccion pero en este caso usamos la ip 192.168."numero de grupo".2 que en este caso es el grupo 5.

Debemos hacer algo similar en otro archivo, para hacer lo ejecutamos el siguiente comando:
```bash
$ sudo nano /etc/dhcpcd.conf
```
Buscamos las siguientes lineas en este archivo(sacandoles el # para que dejen de estar como comentario) y les ponemos las ip que les correspondan:
```bash
interface eth0
static ip_address=192.169.0.2/24
static routers=192.168.0.1
static domain_name_servers=192.169.0.2 8.8.8.8
```
Debemos hacer lo mismo en otro archivo, para hacer lo ejecutamos el siguiente comando:
```bash
$ sudo nano /etc/dhcp/dhcpd.conf
```
Buscamos las siguientes lineas en este archivo(sacandoles el # para que dejen de estar como comentario) y les ponemos las ip que les correspondan:
```bash
subnet 192.169.5.0 netmask 255.255.255.0 {
    range 192.169.5.100 192.169.5.200;
    option routers 192.168.5.1;
    option domain-name-servers 8.8.8.8, 8.8.5.5;
}
```
Debemos hacer lo mismo en otro archivo, para hacer lo ejecutamos el siguiente comando:
```bash
$ sudo nano /etc/default/isc-dhcp-server
```
Remplazaremos las lineas que ya estan escritas:
```bash
INTERFACESv4=”eth0”
INTERFACESv6=”” 
```
Por las siguientes lineas:
```bash
INTERFACES=”eth0”
```
Utilizaremos el siguiente comando para reiniciar el servicio del servidor DHCP y aplicar los nuevos ajustes:
```bash
$ sudo service isc-dhcp-server restart
```
Luego utilizaremos el siguiente comando para habilitar el servidor DHCP:
```bash
$ sudo systemctl enable isc-dhcp-server
```
Y a continuación reiniciaremos el Raspberry para que se le asigne su nueva ip. Para el reinicio utilizamos el siguiente comando:
```bash
$ reboot
```
Una ves reiniciado utilizamos el siguiente comando para iniciar el servidor DHCP:
```bash
$ sudo systemctl start isc-dhcp-server
```
# Conclusión:
El informe proporciona una documentación detallada de los pasos necesarios para configurar correctamente un servidor DHCP en una Raspberry Pi, lo que facilita la comprensión y ejecución del proceso.