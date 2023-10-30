# Informe Grupo 5
## TP FTP
## Alumnos: Miller Derek, Prosdocimo Renzo, Tempesti Mateo, Weigandt Timoteo
Caurto trabajo
Se retiran los materiales del armario, se conectan los perisfericos (teclado, mouse y monitor) a la Raspberry, tambien se conecta a un tomacorriente por medio de un cable con punta micro USB y a la red de internet mediante el cable LAN.  

**LOS SIGUIENTES COMANDOS FUERON EJECUTADOS EN LA RASPBERRY**
Para comenzar primero tenemos que descargar el servidor vsftpd
```bash
$ sudo apt-get install vsftpd
```
Despues que se termina de descargar abrimos la configuracion 
```bash
$ sudo nano/etc/vsftpd.conf
```
Despues tenemos que descomentar las siguientes dos lineas para la escritura de archvios
```bash
$ loca_enable = Yes
$ write_enable = YES
```
Reiniciamos el servidor
```bash 
$ sudo service vsftpd restartCliente FTP
```
Una vez instalado el FTP hay que corroborar si funciona, descargando filezilla
```bash
$ sudo apt install filezilla
```
En Los siguientes camos

- Servidor: Ponemos la ip de la Raspberry
- nombre de usuario: en este caso grupo5 (por defecto "pi")
- contraseña: en este caso grupo5  (por defecto "raspberry")

Una vez rellenados esos campos corroboramos el funcionamiento del servidor FTP mandando archivos de un usuario al otro.

### Conclusion:
Se instaló y configuro el servidor FTP, tambien utilizando el filezilla se corroboro si el servidor funciona correctamente pasando archivos desde la raspberry a la pc.