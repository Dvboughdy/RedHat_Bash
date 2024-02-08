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


### 1.4 Ver el contenido del archivo comprimido `.tar` sin necesidad de descomprimirlo

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



# Topic 3: Manejo de procesos en la terminal 

## 1. Ver los procesos activos en la terminal (`ps`)
El comando `ps` muestra una tabla sencilla de entender con los procesos activos, donde la primera columna representa el process ID (`PID`) y la última columna el nombre del proceso (`CMD`).

## 2. Ver procesos más detallados (`top`)
Para obtener una lista más detallada de los procesos, incluyendo su consumo de **CPU** y **RAM**, así como el usuario que lo inició en tiempo real, utilizamos el comando `top`. Además, podemos filtrar por usuario presionando "`u`" y acceder a la ayuda presionando "`h`". Para salir, presionamos "`q`".

## 3. Ver procesos más detallados (`htop`)
El comando `htop` ofrece una interfaz más intuitiva y amigable para evaluar los procesos del administrador de tareas. Funciona de manera similar a `top` con los shortcuts mencionados.

![](https://i.postimg.cc/xdNmXn1c/imagen-2024-02-08-181451444.png)

## 4. Matar un proceso (`kill`) o (`pkill`)
Para finalizar un proceso, utilizamos el comando `kill` seguido del (`PID`) del proceso que queremos terminar. 

> [!NOTE]
> 
> En sistemas Windows, podemos usar la terminal para cerrar aplicaciones, pero en **WSL** solo podemos acceder a los procesos ejecutados en la terminal.

- **Ejemplo de eliminación de un proceso**
![](https://i.postimg.cc/4dzh1PtG/imagen-2024-02-08-181527486.png)

En este caso si ejecuto el comando `kill -595` voy a cerrar la terminal.

- Por otro lado se puede forzar la terminación de un proceso utilizando la señal **"-9"** con `kill -9 PID` o `killall -9 PID/NAME` que terminara con el proceso de forma inmediata.


### 4.1 Dato importante de `kill -9` o `killall -9`
> [!CAUTION]
> La señal `-9` envía una señal **SIGKILL** indicando al servicio que se cierre de inmediato. **Aunque es efectivo para terminar procesos rebeldes, debe usarse con precaución**, ya que omite el proceso de apagado estándar y puede resultar en la pérdida de datos no guardados.

### 4.2 Opción alternativa con `pkill`:
El comando 
```bash
`pkill -name`
 pkill -9 PNAME o CMD
```
Terminara un proceso especificando el nombre del proceso que se desea eliminar.

### 4.3 Dato importante de `kill` en htop:**
> [!IMPORTANT]
> 
> En htop, al solicitar `kill` de un proceso con `F9`, dice en la parte inferior **enter** | **send** || **Esc** | **Cancel**, y al mover las teclas hacia arriba y abajo permite seleccionar que señal de terminación enviar… puede presionarse directamente el numero de la señal y luego enter o buscar con las flechas. Detalles pqueños de los Sistemas Operativos (Windows es PEOR en cierto modo, aunque powershell soluciona mucho, y tiene una opción o ‘flag’ para forzar cierre).



# Topic 4: Procesos en foreground y background

## 1. Proceso en "Foreground"
- Un proceso que se muestra activamente en la terminal se considera en foreground. 
- **Ejemplo**
  
  Cuando escribimos un texto usando 
  ```bash
  cat > mi_nota.txt`
  ```
  la terminal espera nuestra entrada.

## 1.1 Suspensión de Proceso y enviarlo a Background
Podemos escribir algo y después terminar el input del texto con **CTRL + D**, pero en esta ocasión no haremos eso. 

- Lo que queremos hacer será suspender el proceso, esto lo podemos hacer con **CTRL + Z**. El resultado que nos mostrará la terminal deberá ser uno donde nos indique la suspensión del comando `cat` moviendo este proceso detenido al **background**.

## 2. Acceso a los procesos detenidos en el "Background" con `jobs`

Utilizamos el comando `jobs` para ver los procesos en background y su número de trabajo.

## 2.1 Traer procesos del "back" al "foreground" con `fg` 
- Para traer un proceso de background al foreground, usamos el comando `fg ` seguido del número de trabajo del proceso.
- **Ejemplo**
```bash
fg 1`
```
- En ZSH, el formato sería `fg %1` debido a la interpretación de las wildcards.
  
  Una vez enviado al foreground veremos como se activa la ejecución del comando en la terminal y podremos seguir escribiendo nuestra nota. Recuerda que una vez terminemos de escribir presionamos **CTRL + D** para terminar el input y guardar.

Cuando se guarda el proceso de `cat`, el proceso por fin termina y si se usa `jobs` no mostrará ningún trabajo en **background**.


## 3. Otras Formas de Enviar al Background
### 3.1 Agregar el operador de control `&` al final de un comando 
Este operador enviara el proceso directamente al **background**.
- **Ejemplo**
```bash
cat > mi_nota.txt &
```

### 3.2 Utilizar el comando `bg`
Este sirve de manera similar que `fg` solo que en vez de traerlo al **foreground** este lleva un trabajo al **background**

- **Ejemplo**
```bash
bg 1
```

### 3.2.1 Ejemplo Práctico de como usar el comando `bg`

Al abrir un programa de interfaz gráfica desde la terminal, como Google Chrome 
```
google-chrome-stable
```
Este se ejecuta pero no deja hacer ninguna otra tarea ya que la ventana del navegador está abierta:

- Para ello se puede suspender el proceso con `CTRL+Z` y al revisar con jobs lo mostrara en pausa con el numero de trabajo correspondiente en este caso [1].
  
  ![](https://i.postimg.cc/bYK8HPgQ/imagen-2024-02-08-184621290.png)


- Para poder correr nuevamente el navegador y a su vez seguir trabajando en la terminal se debe reactivar el proceso usando 
```bash
bg 1`
```
moviendolo  al background y continuar trabajando en la terminal mientras el programa se ejecuta en segundo plano.

![](https://i.postimg.cc/fTms8Pq1/imagen-2024-02-08-184649101.png)

> [!NOTE] Este conocimiento es útil cuando necesitamos ejecutar varios comandos en paralelo con una sola terminal. Con estos métodos, podemos gestionar eficazmente los procesos según nuestras necesidades.