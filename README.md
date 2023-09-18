# Informe Grupo 5
## TP Raspberry y SSH
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