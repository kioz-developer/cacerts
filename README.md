## (Java Cacerts)

### Manual para crear el almacén de certificados de Java

### Objetivo

El objetivo de este documento es describir los pasos necesarios para crear el almacén de certificados de Java, necesario para consumir algunos servicios:

### Para crear el almacén debes seguir los siguientes pasos:

Paso 1. Descargar el certificado, puedes usar el [asistente](https://github.com/kioz-developer/cacerts/blob/master/chrome/README.md) para exportar certificados de Google Chrome. 

Paso 2. Pasar el certificado (.cer) a formato PEM (.pem) utilizando la terminal de Linux: 
```sh
$ openssl x509 -inform der -in [REPLACE_NAME].cer -out [REPLACE_NAME].pem
```

Paso 3. Importar el certificado (.pem) a un almacén de certificados de Java utilizando la terminal de Linux, ingresar a la carpeta bin del JRE o JDK, *recuerda que se te pedida definir una contraseña para el almacén*:

```sh
$ cd /opt/java/[YOUR_JRE_JDK]/bin
$ ./keytool -keystore cacerts -importcert -alias [REPLACE_NAME] -file [REPLACE_NAME].pem
```
**Importante:** el usuario debe tener privilegios para poder crear o editar el archivo cacerts

Paso 4. Validamos la existencia del certificado dentro del Almacén (Owner: CN=[YOUR_DOMAIN]]) utilizando la terminal de Linux: 
```sh
$ ./keytool -list -v -keystore cacerts
```

### [Errores comunes](https://github.com/kioz-developer/cacerts/blob/master/errores/README.md) 
