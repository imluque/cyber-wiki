[[Aircrack-ng]]

> ⚠️ **Aviso**  
La información descrita a continuación se estudia con fines educativos para comprender cómo funcionan las auditorías de redes inalámbricas y así poder **prevenir ataques y mejorar la seguridad**.
Estas técnicas solo deben aplicarse en redes propias o con autorización expresa.

![[isoflow-export-2025-12-26T11_36_50.286Z.png]]

## 0. Requisitos

- Descargar la wordlist `rockyou.txt`
- Entorno linux de pruebas, en este caso uso Kali, mas información en: https://www.kali.org/
- Adaptador de wifi 
- Estar al alcance físico de la señal victima


------------------------------------------------------------------------
## 1. Instalación de herramientas

-   Instalar `aircrack-ng` en nuestro entorno de pruebas: https://github.com/aircrack-ng/aircrack-ng


------------------------------------------------------------------------
## 2. Identificación de interfaces

-   Identificar:
  -   Adaptador Wi-Fi del dispositivo
  -   Red Wi-Fi a testear

```
ifconfig
``` 


------------------------------------------------------------------------
## 3. Activar modo monitor

-   Activar el modo monitor en el adaptador Wi-Fi
  
```
airmon-ng start <adaptador>
```

-   Se crea una nueva interfaz en modo monitor (normalmente `<adaptador>mon`, por ejemplo `wlan0mon`)


------------------------------------------------------------------------
## 4. Enumerar redes Wi-Fi cercanas

```
airodump-ng <adaptador_mon>
```


------------------------------------------------------------------------
## 5. Selección de la red objetivo

-   Anotar:
    -   **BSSID** del punto de acceso
        `xx:xx:xx:xx:xx:xx`
    -   **Canal (CH)**


------------------------------------------------------------------------
## 6. Captura de tráfico

```
airodump-ng -c <canal> --bssid xx:xx:xx:xx:xx:xx -w fichero <adaptador_mon>
```

-   Se genera el archivo de captura (`.cap`)
-  `-c`: Selecciona el canal por el que viaja el router victima
- `--bssid`: BSSID router victima


------------------------------------------------------------------------
## 7. Generación de tráfico (nuevo terminal)

```
aireplay-ng -0 9 -a xx:xx:xx:xx:xx:xx -c xx:xx:xx:xx:xx:xx <adaptador_mon>
```

-   `-a` → BSSID del punto de acceso WPA handshake 
-   `-c` → BSSID de la estación (cliente) STATION

Con este comando intentamos suplantar ese handshake para poder falsificar la entrada hasta que podamos establecer conexión, este comando se deberá ejecutar las veces necesarias hasta conectar. 

------------------------------------------------------------------------
## 8. Ataque de diccionario

```
aircrack-ng -b xx:xx:xx:xx:xx:xx -w rockyou.txt auditoria01.cap
```
  
- BSSID correspondiente al punto de acceso WPA handshake
- Diccionario preferido con opción -w `rockyou.txt`
- Archivo `.cap` generado previamente

Con este comando esperaremos a forzar la contraseña con las contraseñas generadas del “rockyou.txt” junto con el tráfico interceptado “auditoria01.cap” para poder colarnos en la red wifi.

Este comando dejaremos que esté ejecutado aprox 30min, si no consigue la contraseña tendremos que ejecutar de nuevo el comando y así sucesivamente hasta lograr crackear la contraseña del router víctima.

------------------------------------------------------------------------
## 9. Finalización

- Desconectamos el adaptador en modo monitor

``` 
airmon-ng stop <adaptador_mon>
```


## 10. Conclusiones

Este procedimiento resume las fases básicas de una auditoría Wi-Fi orientada a evaluar la fortaleza de la seguridad de una red inalámbrica. A través de la identificación del entorno, la captura de tráfico y el análisis posterior, se pone de manifiesto que la seguridad de una red depende en gran medida de la calidad de su configuración y, especialmente, de la robustez de su contraseña.

El uso de herramientas automatizadas y diccionarios conocidos demuestra que las contraseñas débiles o predecibles pueden ser comprometidas con relativa facilidad, mientras que claves largas y complejas resisten este tipo de ataques. Por ello, estas prácticas resultan útiles para concienciar sobre la importancia de aplicar buenas medidas de seguridad y para validar, en un entorno controlado, si una red cumple con los requisitos mínimos de protección.

En definitiva, una auditoría correctamente realizada permite detectar vulnerabilidades, reforzar la seguridad de la red y reducir el riesgo de accesos no autorizados.
