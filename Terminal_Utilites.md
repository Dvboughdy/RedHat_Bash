# Topic 1: Utilidades de la red


## 1. Configuración de dispositivos `ifconfig` y `netstat` 
1. Con `ifconfig` se puede obtener información sobre la configuración de red de un dispositivo, incluyendo el nombre del dispositivo que en este caso es `etho`, su dirección IPv4 e IPv6, así como su máscara de red.

2. También se puede usar el comando `netstat` para visualizar esta información de manera más amigable en forma de tabla.

![](https://i.postimg.cc/3NTP9WyG/imagen-2024-02-07-213637874.png)

## 2. Envío de solicitudes a una página (`ping`): 
El comando `ping` permite verificar la disponibilidad de una página desde una dirección IP específica. Para esto escribimos el comando seguido de la `URL` a la que queremos acceder.

**Ejemplo:**
```bash
ping www.google.com
```
De esta salida se obtiene
- La dirección IP de esa URL

- Cuanto tiempo tardó en responder la página medida en milisegundos y

- En la parte de abajo se tiene el total de **paquetes que se enviaron**, **los paquetes que se recibieron**, **el porcentaje de paquetes perdidos** y **el tiempo de respuesta promedio de las consultas**.

> [!NOTE]
> Por defecto, el comando se ejecutará indefinidamente, así que se debe detener con `Ctrl + C`.

### 2.1 Limitar el numero de paquetes con (`-c`) 
Este flag permite limitar el número de paquetes enviados y especificar el tamaño de los paquetes por enviar.
**Ejemplo:**

```bash
ping -c 4 www.google.com
```
### 2.2 Especificar el tamaño de los paquetes (`-s`)

Para probar la conectividad con paquetes de diferentes tamaños se utiliza la opción `-s` seguido del tamaño del paquete que desees usar. **El tamaño debe ser en bytes.**

Para hacer pruebas con paquetes de 20 bytes se usa el comando:
```bash
ping -s 20 www.google.com
```

## 3. Obtención de archivos de una página (`curl` | `wget`)
Estos comandos se usan para obtener archivos de una página web o dirección IP.
- `curl` muestra la información en la consola y luego se debe guardar en un  documento .html que almacene el codigo traido de la URL en este caso de la URL `www.google.com` pero en desorden.

  ![](https://i.postimg.cc/Bb2NYgWZ/imagen-2024-02-07-220224215.png)

  Pero al crearse un archivo con un codigo sin formateo en su estructura se recomienda a usar el comando `wget`

- `wget` guarda la información en un archivo especificado .
  
  ![](https://i.postimg.cc/65NM7DR8/imagen-2024-02-07-220247015.png)

  La última línea de la salida del comando `wget` dice que la información fue guardada en el archivo "`index.html`", el cual podemos ver al listar los archivos.
  
### 3.1 Específicar varias direcciones para descargar varias páginas al mismo tiempo en `wget`.

**Ejemplo:** `wget www.google.com www.platzi.com`

![](https://i.postimg.cc/d1y93BVR/imagen-2024-02-07-220342872.png)

Aquí vemos como se guardó la página de Google en "index.html.1" y la de Platzi en "index.html.2".

## 4. Ruta de acceso a la página (`traceroute`) 
`traceroute`permite visualizar los servidores intermediarios entre la computadora del usuario y el servidor de una página web.

![](https://i.postimg.cc/DygPSmnN/imagen-2024-02-07-220403056.png)

### 4.1 Caso particular de instalación de las herramientas de red

Para poder ejecutar el comando traceroute se deben instalar los siguientes paquetes ejecutables

- Installar herramientas de red:
```bash
sudo apt-get install net-tools
```
- Instalar traceroute:
```bash
sudo apt-get install traceroute
```


# Topic 2: Comprimiendo archivos desde la terminal 

## 1. Comprimiendo archivos con formato `.tar`
Para comprimir con este formato en la terminal usamos el comando `tar` que tiene ciertas opciones
**Sintaxis:**
```bash
tar [opciones] [nombreDelArchivoComprimido] [archivoAComprimir]
```

### 1.1 Comprimir`-c`
En todos los casos hay que usar la opción `-f` para indicar que estamos comprimiendo o descomprimiendo archivos.
![](https://i.postimg.cc/4y6cD4JV/imagen-2024-02-07-225944579.png)

- **Ejemplo:** 
```bash
tar -cf compressed.tar Documents/toCompress/
```
Al listar se podra ver un archivo con el nombre compressed.tar que corresponde al comprimido

### 1.2 La opción Verbose `-v` 
Se utiliza para ver el progreso de la compresión. (Tambien se puede reconocer como `--verbose`)
![](https://i.postimg.cc/SxN9PpHY/imagen-2024-02-07-230006783.png)

### 1.3 Comprimir archivos en formato "`.tar.gz`" o "`.tgz`" con la opción `-z`
Este es una versión extendida del formato tradicional de compresión ".zip" que puede manejar y comprimir archivos más grandes.
![](https://i.postimg.cc/J0LD5wbn/imagen-2024-02-07-230057383.png)


### 1.4 Ver el contenido del archivo comprimido.tar sin necesidad de descomprimirlo

Para ver el contenido de un archivo `.tar` sin necesidad de descomprimirlo, se puede ejecutar el comando:
```bash
tar tvf archivo.tar
tar tvf archivo.tar.gz
```

### 1.5 Descomprimiendo archivos `.tar` con la opción `-x`
- Se usa el comando `tar` con la opción `-x` para descomprimir.
```bash
tar -xvf compressed.tar
```
- Si el archivo está en formato "`.tar.gz`" o "`.tgz`", se agrega la opción `-z`.
```bash
tar -xzvf compressed.tar.gz
```


## 2. Comprimiendo archivos `.zip`
- Se emplea el comando `zip` junto con la opción `-r` de **"recursive"** para comprimir carpetas y su contenido.
![](https://i.postimg.cc/j20g6jg7/imagen-2024-02-07-231056185.png)


### 2.1 Ver el contenido del archivo comprimido.zip sin necesidad de descomprimirlo
```bash
unzip -l mi_archivo.zip
```

### 2.2 Descomprimiendo archivos `.zip` con `unzip`
- Se utiliza el comando `unzip` seguido del nombre del archivo a descomprimir.

```bash
# Ejemplo
unzip compressed.zip
```

## 3. Comprimiendo archivos `.rar`
- Se usa el comando `rar` con la opción `-r` ademas del flag `a` de "**agregation**" para comprimir carpetas y su contenido.
![](https://i.postimg.cc/gJP8N6pm/imagen-2024-02-07-231310975.png)

### 3.1 Ver el contenido del archivo comprimido.rar sin necesidad de descomprimirlo
```bash
unrar l mi_archivo.rar
```

### 3.2 Descomprimiendo archivos `.rar` con `unrar`
- Se emplea el comando `unrar` seguido del flag `x` para descomprimir.
```bash
# Ejemplo
unrar x compressed.zip
```