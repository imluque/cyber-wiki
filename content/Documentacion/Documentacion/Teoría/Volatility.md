
Sirve para sacar información a través de los metadatos de memoria RAM, esto lo podemos analizar de un fichero .img

Usamos el parámetro "imageinfo" para saber el profile, versión del SO. Esto nos ayudara a usar volatility adecuadamente para sacar la información del .img dependiendo de que sistema operativo tenga o se identifique.

Sabiendo el profile podemos usar otros parámetros para explotar y sacar información del fichero

```
volatility -f "imagen.img" imageinfo
```

Si queremos ver los usuarios existentes en esta imagen cogeremos el "SuggestedProfile(s)" y utilizaremos el hashdump

```
volatility -f "imagen.img" hashdump --profile="Win7SPOx86"
```

para analizar los puertos usaremos abiertos de la imagen usaremos netscan

```
volatility -f "imagen.img" --profile="Win7SPOx86" netscan
```

En este caso `Win7SPOx86` es el profile de un Windows7x86.

Mas info del framework: https://github.com/volatilityfoundation/volatility/blob/master/README.txt