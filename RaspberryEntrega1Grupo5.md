# Informe Grupo 5
## TP Raspberry y SSH
## Alumnos: Miller Derek, Prosdocimo Renzo, Tempesti Mateo, Weigandt Timoteo
Primer Trabajo:  
Se retiran los materiales del armario, se conectan los perisfericos (teclado, mouse y monitor) a la Raspberry, tambien se conecta a un tomacorriente por medio de un cable con punta micro USB y a la red de internet mediante el cable LAN.  

Para poder comenzar a configurar la Raspberry,  se debe descargar el sistema operativo [Raspberry](https://www.raspberrypi.org/) mediante una tarjeta SD, en este caso en especifico instalamos el 64bits no desktop.  

Luego de terminar con la instalacion y configuracion del sistema operativo, se inicializa el servidor SSH en la Raspberry y se conecta una computadora con SSH mediante el usuario y la ip de la Raspberry.

Los comandos que se utilizan para la inicializacion del servidor SSH en nuestra Raspberry, son los siguientes:
```bash
$ sudo apt-get install openssh-server
```
Este comando instala el servidor SSH en la Raspberry.
```bash
$ sudo systemctl start ssh
```
Este comando inicia el servidor SSH en la Raspberry.
```bash 
$ sudo systemctl enable ssh
```
Este comando habilita el servidor SSH en la Raspberry.

Una vez iniciado y habilitado el servidor SSH, se puede conectar a la Raspberry desde una computadora con SSH mediante el usuario y la ip de la Raspberry. En nuestra terminal ponemos:
```bash
$ ssh 'usuarioDeLaRaspberry'@'IPDeLaRaspberry'
```
Para conseguir la ip de la raspberry se puede ejecutar el siguiente comando:
```bash
$ hostname -I
```
consigue el DNS y define el hostname del sistema
-i (hostname): opción que devuelve la IP

Para conectar el raspberry con la computadora  utilizamos el siguiente comando:
```bash
$ ssh [usuario]@[IP]
```
es un comando usado para ingresar en otra computadora y ejecutar comandos desde ella (Usuario e ip deben ser remplazados por los reales)

### Conclusion
Se instalo el sistema operativo necesario y se realizo el proceso que permitió la conexión de dos dispositivos a través de un SSH.