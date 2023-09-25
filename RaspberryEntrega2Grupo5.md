# Informe Grupo 5
## TP Raspberry y SSH
## Alumnos: Miller Derek, Prosdocimo Renzo, Tempesti Mateo, Weigandt Timoteo
Segundo Trabajo:  
Se retiran los materiales del armario, se conectan los perisfericos (teclado, mouse y monitor) a la Raspberry, tambien se conecta a un tomacorriente por medio de un cable con punta micro USB y a la red de internet mediante el cable LAN.  

**LOS SIGUIENTES COMANDOS FUERON EJECUTADOS EN LA RASPBERRY**

Para comenzar con la consigna se instala [xorg](https://www.x.org/wiki/), para instalarlo, se utilizo el siguiente comando:
```bash
$ sudo apt install xorg
```
Una vez instalado xorg, se deben cambiar ciertos parametros dentro de los archivos de configuracion de ssh. Para lograr esto se ejecuta el siguiente comando, el cual abre un editor de texto en la terminal, con el cual podremos cambiar los parametros necesarios:
```bash
$ sudo nano /etc/ssh/ssh_config
```
Al ingresar a este archivo, deberemos buscar las siguientes lineas:
```bash
#  ForwardX11 yes
#  ForwardX11Trusted no
```
Y cambiarlas por las siguientes lineas: 
```bash
ForwardX11 yes
ForwardX11Trusted yes
```
Una vez modificadas las lineas de configuracion, para guardar el archivo se debe tocal Ctrl+X y luego la tecla Y para confirmar los cambios, luego enter para confirmar que el nombre del archivo se mantenga como estaba previamente.

Debemos hacer algo similar en otro archivo, para hacer lo ejecutamos el siguiente comando
```bash
$ sudo nano /etc/ssh/sshd_config
```
Buscamos las siguientes lineas en este archivo
```bash
#  ForwardX11 yes
#  ForwardX11Trusted no
```
Y las modificamos por las siguientes lineas
```bash
ForwardX11 yes
ForwardX11Trusted yes
```
Para guardar el archivo, se debe tocar Ctrl+X y luego la tecla Y para confirmar los cambios, luego enter para confirmar que el nombre del archivo se mantenga como estaba previamente.  
Una vez terminados los cambios, se debe reiniciar el servidor SSH para que se actualicen los cambios.
```bash
$ sudo systemctl restart ssh
```
Para poder probar que el programa funciona, podemos hacer lo siguiente, una vez reiniciado el servidor SSH, instalamos [calibre]() en nuestra raspberry con el siguiente comando:
```bash
$ sudo apt install calibre
```
Al finalizar la instalacion, se conecta la Raspberry desde una computadora con SSH mediante el usuario y la ip de la Raspberry. En nuestra terminal ponemos:
```bash
$ ssh -X 'usuarioDeLaRaspberry'@'IPDeLaRaspberry'
```
El parametro -X indica que se conectara con el protocolo SSH X11,
 para conseguir la ip de la raspberry se puede ejecutar el siguiente comando:
```bash
$ hostname -I
```
Luego desde la raspberry, creamos un archivo .txt con el nombre que querramos, para demostrar le pondremos el nombre ej.txt
```bash
$ touch ej.txt
```
Luego desde nuestra computadora conectada con nuestra raspberry ejecutamos el siguiente comando:
```bash
$ gedit ej.txt
```
Luego de ejecutar esto, se va a abrir un editor de texto, donde se va a escribir el contenido que queramos. En este caso, se va a escribir el siguiente contenido:
```bash
Hola mundo
```
Cuando se guarda el archivo, al ejecutar el comando
```bash
$ sudo nano ej.txt
```
se va a poder ver los cambios realizados desde la computadora en la raspberry.  
### Conclusion:
Se instaló y configuro el programa xorg. Tambien se instaló a modo de prueba y ejemplo el programa calibre y se utilizo para modificar un archivo txt desde una computadora y que los cambios se vean reflejados en la raspberry.