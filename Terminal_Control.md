# Redirecciones en la terminal

## ¿Qué son las entradas y salidas de la terminal?
Entradas y salidas: Se refieren al flujo de datos generado al interactuar con comandos en la terminal.

## Standard Input `(stdin)` y Standard Output `(stdout)`
Términos comunes para describir las entradas y salidas, abreviados como **stdin** y **stdout**.

## ¿Qué son los file descriptors?
Números que identifican recursos en la terminal. En la shell, hay 3 principales:
- 0 para Standard Input (**stdin**)
- 1 para Standard Output (**stdout**)
- 2 para Standard Error (**sterror**)
  
![](https://i.postimg.cc/kgKHP7gJ/imagen-2023-12-26-180116450.png)

## ¿Cómo usar el operador de redirección `(>)`?

### Redirección de `Standard Output`:
Utiliza `>` para redirigir el **Standard Output** a un archivo. 

Ejemplo: 
```bash
ls -l > output.txt.
```
![](https://i.postimg.cc/tTxkW5nX/imagen-2023-12-26-180917302.png)

### Concatenación de `Standard Output`: 
Para añadir a un archivo existente sin sobrescribir, utiliza >>. 
Ejemplo:
```bash
 ls -l >> output.txt.
```
![](https://i.postimg.cc/J73c8tbd/imagen-2023-12-26-180933354.png)

## Redirección de Errores `(2>|2>&1)`

### Redirección de `Standard Error` con descriptor `2>`
Especifica el file descriptor 2 para redirigir errores.

Ejemplo:

![](https://i.postimg.cc/tg78DYsT/imagen-2023-12-26-205618440.png)

### Redirección de `Standard Error` fucionado con `Standard Output`:
Especifica el file descriptor 2 para redirigir errores y luego el file descriptor 1 para redirigir a un archivo de salida.

Ejemplo: 
```bash
ls -l > output.txt 2>&1.
```
![](https://i.postimg.cc/XJCmSmc6/imagen-2023-12-26-205634015.png)

## Redireccionamiento de Entrada o `Standard Input` usando `(<)`
###  Alimentar un Comando desde un Archivo: 
Usa `<` para proporcionar entrada desde un archivo. 
Ejemplo: 
```bash
sort < lista_de_servidores.txt
uniq < lista_ips.txt
```

### Redirección de `stdin` y `stdout` en el mismo comando: 
Combina `<` y `>`. 
Ejemplo:
```bash
sort < lista_desordenada.txt > lista_ordenada.txt.
```
![](https://i.postimg.cc/TYR7CpS6/imagen-2023-12-26-205759467.png)


# Redirecciones con Pipe Operators en la Terminal

## Pipe Operator
Es un operador que permite tomar la salida de un comando y usarla como entrada para otro comando.

## Comandos de Pipe Operator

### Unir cadenas de texto (`cat`)
Permite concatenar la salida de varios comandos, creando una lista de archivos de diferentes carpetas.

Ejemplo: 
```bash
cat Images/* SecretosDeEstado/*
```
![](https://i.postimg.cc/9Q0xHsCg/imagen-2023-12-26-205822597.png)

### Crear un archivo con base en una salida (`tee`)
Guarda la salida de un comando en un archivo. Útil para conservar la salida de un conjunto de comandos en un archivo llamado "archivos.txt".

Ejemplo: 
```bash
cat images.txt secretosDeEstado.txt | tee archivos.txt
```
![](https://i.postimg.cc/fyMK2r8K/imagen-2023-12-26-205941238.png)

### Organizar archivos con (`sort`)
Organiza alfabéticamente la salida de un comando, en este caso, la lista de archivos de la carpeta actual. Luego, crea un archivo llamado "archivosHome.txt" con la salida organizada.

Ejemplo: 
```bash
ls | sort | tee archivosHome.txt
```
![](https://i.postimg.cc/cCTcVBjN/imagen-2023-12-26-205953622.png)

### Ver la información desde un entorno editable (`less`)
Permite ver la salida de un comando en un entorno editable, facilitando la inspección de la información.
Ejemplo: 
```bash
ls archivosHome.txt | less
```
![](https://i.postimg.cc/1zxD7dtq/imagen-2023-12-26-210228469.png)

### Comando visual `cowsay` y `lolcat`
`cowsay` y `lolcat` son comandos que añaden un toque divertido y colorido a tu terminal.

![](https://i.postimg.cc/BbvF19hd/imagen-2023-12-26-210307446.png)

- **cowsay**: Este comando coloca un dibujo de una vaca (o de otro animal, dependiendo de las opciones) junto con un mensaje que le proporcionas. Es simplemente una manera lúdica de mostrar mensajes en la terminal. Aquí tienes un ejemplo básico:
- 
```bash
cowsay "Hola, soy una vaca"
```
La salida podría ser algo como:
 _______________
< Hola, soy una vaca >
 ---------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
Puedes instalar cowsay en sistemas basados en Debian (como Ubuntu) usando:
```bash
sudo apt-get install cowsay
```
- **lolcat**: Este comando colorea la salida de otros comandos en la terminal. Puedes "pipear" la salida de un comando a lolcat, y verás que el texto se presenta con colores del arco iris. Aquí tienes un ejemplo básico:

```bash
ls -l | lolcat
```
Esto mostrará la lista de archivos del directorio actual con colores llamativos. Puedes instalar lolcat en sistemas basados en Debian con:

```bash
sudo apt-get install lolcat
```


# Encadenando comandos: Operadores de control

Los operadores de control son símbolos reservados por la terminal que facilitan el encadenamiento de comandos.

## Comandos en la misma línea (`;`)
Permite ejecutar varios comandos en la misma línea, separados por `;`.

Ejemplo:
```bash
mkdir ProyectosSecretos; ls; date
```

## Comandos asíncronos (`&`)
Permite ejecutar varios comandos al mismo tiempo, utilizando el operador `&`. Cada comando se ejecuta en un hilo separado.

Ejemplo: 
```bash
date & echo "Hola" & cal
```
![](https://i.postimg.cc/K8t1j8G1/imagen-2023-12-26-210512406.png)

- En la salida podemos ver que en la primera línea dice `[1] 349` y en la tercera dice `[2] 350`, esto significa que se crearon dos hilos para ejecutar los 3 comandos que se le dieron.
- 
- El primero, con el id 349, se usó para ejecutar el comando `date` y el segundo, con el id 350 se usó para ejecutar los comandos `echo` y `cal`.
## Comandos con condicionales

### Condición and (`&&`)
Los comandos se ejecutan en orden y solo si el comando anterior se ejecuta correctamente.
> [!NOTE]
> 
> **Los comandos se ejecutan en orden, y cada uno depende del éxito del anterior.**

Ejemplo:
```bash
cd lp && mkdir Comida
```
![](https://i.postimg.cc/mkMP9LYp/imagen-2023-12-26-210753663.png)

Ejemplo: 
```bash
cd ProyectosSecretos/ && touch ProyectoExplosivo.txt && ls
```
![](https://i.postimg.cc/k59BbPGf/imagen-2023-12-26-210523581.png)

### Condicional or (`||`)
Los comandos se prueban en orden, y se ejecuta el primero que tenga éxito, sin importar si los anteriores fallan.

Ejemplo: 
```bash
cd ProyectosSecretos/ || cambia-carpeta ProyectosSecretos/
```
![](https://i.postimg.cc/x1GdYp5H/imagen-2023-12-26-210622172.png)

## Combinando operadores de control
Se combinan operadores de control. Si el primer comando falla, se ejecuta el segundo. Luego, si el segundo tiene éxito, se ejecuta el tercero.

Ejemplo:
```bash
cd ProyectosSecretos/ || cambia-carpeta ProyectosSecretos/ && mkdir ProyectoIncreible
```
![](https://i.postimg.cc/63q6rWXL/imagen-2023-12-26-210636251.png)

## Más funcionalidades
Se presentan otras funcionalidades de los operadores de control, como el operador ! que invierte el resultado de un comando.
![](https://i.postimg.cc/prZt43RX/imagen-2023-12-26-211022375.png)

## Operadores de control con Pipe Operators
![](https://i.postimg.cc/LXjSBnWP/imagen-2023-12-26-211009127.png)

# Manejo de permisos
Los permisos en un sistema operativo definen las acciones que cada usuario puede realizar sobre archivos y carpetas. Al utilizar el comando ls -l, la primera columna que aparece representa estos permisos.

## Tipos de archivos:
- **Archivo ordinario (`-`)**: Representa un archivo estándar.
- **Directorio (`d`)**: Indica que es un directorio.
- **Enlace o link simbólico (`l`)**: Representa un enlace simbólico.
- **Dispositivo de caracteres (`c`)**: Señala un dispositivo de caracteres.
- **Dispositivo de bloque (`b`)**: Indica un dispositivo de bloque.

![](https://i.postimg.cc/BbNdMDBj/imagen-2023-12-26-211138512.png)

## Permisos de Usuario:
- **Owner (`Dueño`)**: Primeros 3 caracteres representan los permisos del creador del archivo.
- **Group (`Grupo`)**: Siguientes 3 caracteres corresponden al grupo de usuarios asociado al archivo.
- **World (`Otros`)**: Últimos 3 caracteres representan los permisos para usuarios fuera del grupo y el dueño.

![](https://i.postimg.cc/8PK2vRC3/imagen-2023-12-26-211153220.png)
## Tipos de Permisos:
- **r (`read`)**: Permite leer el contenido del archivo.
- **w (`write`)**: Permite editar el contenido, el nombre y los permisos del archivo.
- **x (`execute`)**: Permite ejecutar el archivo si es un programa.
>[!NOTE]
>
> Los permisos se expresan como `rwx`, y un guion (`-`) indica que el permiso no está disponible.
> 
### Estructura de los permisos
![](https://i.postimg.cc/bvbW44Rc/imagen-2023-12-26-211246809.png)

### Modo Octal:
Cada conjunto de permisos se representa con un número octal (0-7), donde:
![](https://i.postimg.cc/9MhK21x4/imagen-2023-12-26-211255948.png)

### Modo simbólico de los permisos
![](https://i.postimg.cc/8zvZCMfL/imagen-2023-12-26-211358872.pngg)

Ejemplo:
> De un directorio `d`, el *owner* tiene permiso de **read** y **write**, el *group* tiene permisos de **write** y **execute** y *world* **no tiene permisos**.

| Type file | Owner | Group | World |
| ------------ | ------------ | ------------ | ------------ |
| **d ⇒ (directory)**    | rw-      | -wx      | ---      |
| Binary      | 110      | 011      | 000      |
| Octtal      | 6     | 3     | 0     |


# Modificando permisos desde la terminal

## ¿Cómo Cambiar Permisos con `chmod`?

### Operadores de asignación o denegación de permisos 
Principalmente se deben tener en cuenta estos operadores
- **+ (`Agrega un permiso`)**.
- **- (`Elimina un permiso`)**.
- **= (`Asigna permisos específicos`)**.

### Forma Simbólica:
Hay que escribir después del comando `chmod` el **símbolo del usuario**, luego el **operador** y por último **el permiso** que quieres **agregar** o **quitar**.

Comando: `chmod [usuario][operador][permiso] [archivo]`.

Ejemplo: 
```bash
chmod g+w ProyectoExplosivo.txt (agrega permisos de escritura al grupo).
```

### Forma Octal:

Representa permisos con números (0-7).

Ejemplo: 
```bash
chmod 755 archivo (permisos rwx r-x r-x).
```
## Observaciones sobre `chmod`
- **Permite Varios cambios simultáneos**: `chmod go+wx [archivo].`

![](https://i.postimg.cc/KcsmtkJ1/imagen-2023-12-26-222811191.png)
- **Permiso específico por usuario mediante el operador de `=`**: `chmod u+r,g=w [archivo].`

![](https://i.postimg.cc/pXhRCW6q/imagen-2023-12-26-222823464.png)
- **Quitar todos los permisos de la forma simbolica**

![](https://i.postimg.cc/xT95K5TR/imagen-2023-12-26-225955100.png)


- **Forma octal para permisos**: `chmod 755`.

![](https://i.postimg.cc/dtrtvQjD/imagen-2023-12-26-223124085.png)

>[!TIP]
>
> **Se pueden crear y editar archivos al instante usando el operador `>` y basta con finalizar la operación con `CTRL+D`**
> 
> ![](https://i.postimg.cc/dt0dsxVz/imagen-2023-12-26-230213347.png)

## Gestión de Usuarios con `whoami` y `su`:
Cuando listamos los archivos con `ls -l` la **`tercera columna` <u>muestra el nombre del usuario que es propietario del archivo</u>** y la **`cuarta columna` <u>muestra el grupo que tiene control sobre el archivo.</u>**

![](https://i.postimg.cc/yYkcTRKt/imagen-2023-12-26-223444184.png)

Para el ejemplo, aparece **"miguelangel"** en ambas columnas porque <u>ese es el usuario que estamos usando y porque el grupo al que pertenece el usuario se llama igual</u> **"miguelangel"**.

- **`whoami`**: Muestra el usuario actual.

- **`su` (Switch User)**: Cambia al usuario especificado.

Ejemplo:
```bash
su root (cambia al superusuario) # Al estar en el superusuario se  solicitara la contraseña de acceso a este.
```
>[!TIP]
>
> ### ¿Qué hacer en caso de olvidar una contraseña?
> 
> Si estás usando Windows Subsystem for Linux (wsl) y se te olvidó la contraseña del root. Sigue estos pasos:
> 
>- Abre el cmd de windows y ejecuta este comando `wsl --user root`. Esto hará que se inicie en la terminal wsl con el usuario root.
>
> - Luego ejecuta el comando `passwd root` el cual te permitirá cambiar la contraseña del usuario root.
> 
> Ya con esto puedes volver a la terminal de wsl y volver a ejecutar el comando `su root`.

## Cambio de Propietario con `chown`:
- **`chown`(Change Owner)**
  
Cambia el propietario de un archivo.

Comando: `chown [usuarioAlQuePertenecerá] [archivo].`

![](https://i.postimg.cc/wMdfKkkW/imagen-2023-12-26-224646955.png)


# Configuración de variables de entorno en la terminal
Las variables de entorno **son herramientas cruciales para agilizar el trabajo y recordar información relevante en el entorno de Linux**, destacando el proceso de configuración y <u>**creación de links simbólicos**</u>, el <u>**manejo de variables de entorno preestablecidas**</u> y la personalización mediante la creación de <u>**alias**</u>.

## ¿Cómo crear un link simbólico?
Estos se caracterizan por ser apuntadores o accesos directos en la terminal.

Comando: `ln -s <ruta> <Nombre>`.

>[1NOTE]
>
> Se comparan con `alias`, **siendo más efectivos al considerarlos como directorios y acceder con `cd Acceso`**.
> 
> ![](https://i.postimg.cc/RFJBHS3n/imagen-2023-12-27-130941941.png)
>
> Se puede visualizar que tiene todos los permisos pero sin valor <u>**(Los links simbólicos como tal no tienen permisos)**</u>

## Variables de Entorno en Linux

Para llamara estar variables se hace uso de comandos como `echo $VARIABLE` para visualizar variables preestablecidas.

Para contemplar todo el set de variables existentes basta con digitar el comando `printenv`

Las variables mas conocidas son:

![](https://i.postimg.cc/kXgzLMs3/imagen-2023-12-27-132220411.png)

> [!IMPORTANT]
> 
> Todas las variables se invocan con un signo de pesos `$`. y ademas por convención, <u> **estas se crean con mayúsculas**</u> 
>
> ![](https://i.postimg.cc/mD46jTkn/imagen-2023-12-27-132325786.png)
> 
> ![](https://i.postimg.cc/tTzvm8V4/imagen-2023-12-27-132340234.png)

## Configuración Personalizada de las variables `.bashrc` y `.zshrc`

1. Ubicar el archivo `.bashrc` en el <u>**home del usuario**</u>, o por otro lado, en caso de tener como ejecutable **OhMyZsh**, el archivo corresponderia a `.zshrc`

2. Visualizar con `ls -la` estos <u>**archivos privados**</u> y ejecutarlos con `code .bashrc` o por el contrario con el **editor interno de `vim`** mediante el comando:

```bash
 vim ~/.zshr 
 vim ~/.bashrc
```
> [!CAUTION]
> 
> Cuando lo abras ten cuidado con lo que tocas, **podrías dañar la shell**, pero desde ahí puedes crear una variable de entorno

**Ejemplo de creación de variable de entorno para ruta en WSL.**

![](https://i.postimg.cc/k4yGgr4S/imagen-2023-12-27-145624028.png)
> [!TIP]
>
> Luego de guarda los cambios, se debe reiniciar la terminal, pero en vez de cerrarla basta con introducir el comando
> ```bash
> source ~/.zshrc
> source ~/.bashrc
> ```
y ya sera posible utilizar la nueva variable creada utilizando la sintaxis del comando mencionada.

![](https://i.postimg.cc/d3H0G8Gt/imagen-2023-12-27-145635260.png)
 O mediante el comando `echo $VARIABLE`

## Creación de `alias`

Los Alias son similares a los links simbolicos que actuan como directorios, pero en vez de declararse directamente como un archivo enlazado a un archivo especifico, se crean directamente en la configuración de la shell, la `bashrc` o `zshrc` similar a las variables

**Ejemplo de creación de alias persistente.**

![](https://i.postimg.cc/rpNRKRZz/imagen-2023-12-27-150709404.png)

Ahora solo basta con escribir el alias creado `cc` y se abrira dicha ruta


# Comandos de busqueda
A veces necesitas localizar varios archivos del mismo tipo que ocupan espacio innecesario en tu disco duro.

Por ejemplo, algunos programas que funcionan desde la consola, como `npm`, guardan sus errores en archivos de extensión **".log"** y si no estás pendiente de eliminarlos se van acumulando en tu disco duro.

## Utilizando el comando de busqueda `find`
Este comando es similar a `which`, `type` o `whereis` que muestran la ruta del archivo, pero con una <u>**serie de opciones para filtrar la busqueda y ser mas especifica y acertada**</u>

Sintaxis: 
- Para consultar en una ruta general solo se utiliza el ./
```bash
find ./ [ruta] [opciones]` 
```
- O basta con solo indicar el `.`

## Búsqueda por Nombre `(-name)`

Ejemplo donde se desea buscar desde el home de la terminal, todos los archivos con extensión `".png"` 

**Sintaxis:** 
```bash
find . [ruta] -name [TipoDeArchivo] 
```

![](https://i.postimg.cc/C5gvbQjS/imagen-2023-12-27-152253423.png)

> [!NOTE]
> ### En el caso de WSL
> Se indica la extensión y el wildcard entre comillas.
>
> ![](https://i.postimg.cc/7Yc2cTWT/imagen-2023-12-27-152553870.png)

## Segmentación por Tipo `(-type)`

También puedes segmentar por el tipo, si es un archivo o si es un directorio utilizando la opción `-type`, el cual acepta 

- `f` para **archivos**
- `d` para **directorios**
- `l` para **enlaces simbólicos**.

**Sintaxis:** 
```bash
find . [ruta] -type [Opción] -name [TipoDeArchivo] 
```
1. Ejemplo donde se buscan todos los archivos que comiencen con la letra **"f"**

![](https://i.postimg.cc/vBNnsgZj/imagen-2023-12-27-153538882.png)

2. A su vez permite el uso de más de una opción separada por comas

![](https://i.postimg.cc/Yjcmv5gz/imagen-2023-12-27-153551620.png)

   3. **EJEMPLO EN `WSL`**

![](https://i.postimg.cc/MpfqPnCH/imagen-2023-12-27-154018523.png)

## Segmentación por Tamaño `(-size)`
Especificación de tamaño con unidad (`c`, `k`, `M`, `G`).

**Ejemplos:**
```bash
find ./ -size 4k
find ./ -size +4k
find ./ -size -4k
```

## Búsqueda de Archivos Vacíos `(-empty`
Si quisiera buscar todas las carpetas vacías, habría que escribir
```bash
find ./ -type d -empty
```
![](https://i.postimg.cc/PxJjDNQd/imagen-2023-12-27-154907947.png)

## Limitar la Búsqueda `(-maxdepth)`o `(-mindepth)`
Puede que no queramos buscar en absolutamente todas las carpetas del sistema, sino que queremos únicamente una parte. Para eso limitamos la profundidad de carpetas a la que el comando debe buscar, esto se hace con la opción `-maxdepth` o `-mindepth` seguido de la profundidad.

**Ejemplos:**
```bash
find ./ -type d -maxdepth 2 
find ./ -type d -mindepth 2
```
![](https://i.postimg.cc/PJcYHL2J/imagen-2023-12-27-155503080.png)

> [!TIP]
>
> Si en la parte superior aparece un `warning` quiere decir que la forma en como esta estructurado el comando no es la correcta, por ello corrobora que este bien estructurado antes de lanzarlo, en este caso la forma correcta de escribir el comando es:
>
> ```bash
> find ./ -mindepth 2 -type f,d -name"*.txt"
> ```

> [!TIP]
>
> Al ser una consulta con mayor peso en su salida, lo mas recomendable es ejecutarlo en una interfaz de navegación que en este caso la mas apropiada es `less`
>

## Consultas practicas para reforzar lo visto

1. Generar una busqueda de` archivos y directorios` con formato `.txt` con una `profundidad maxima de 2` que ademas, se `redireccionen por salida` a un archivo llamado **"mistxtFiles"** y que al final `muestre un mensaje de exito`

-  **Solución:** Este reto se puede lograr de la siguiente manera
![](https://i.postimg.cc/MGTszBYb/imagen-2023-12-27-160823278.png)

  - - Y para visualizar el contenido del archivo nuevo basta con verlo medainte `cat mistxtFiles`
> [!WARNING]
> 
> **Revisar siempre que la sintaxis este escrita de forma correcta**

2. Busca los archivos que tengan extensión ".pdf" con una profundidad mínima de 2. 

-  **Solución:** En este caso solo fue posible con una profundidad maxima debido a la masiva cantidad de archivos incluso algunos con permisos denegados
![](https://i.postimg.cc/nhc8QCkM/imagen-2023-12-27-161751843.png)
![](https://i.postimg.cc/qvmPc4bw/imagen-2023-12-27-161804017.png)

3. Busca todo lo que tenga una letra **"j"** que pese más de `1b`. Luego guarda la salida en un archivo llamado **"LosArchivosJ.txt"** y cuando termine de hacer todo eso imprime un mensaje que diga **"Comando terminado con éxito"**

-  **Solución:** En este caso la **segmentación por tamaño** <u>se posiciona luego de indicar</u> el **nombre del archivo** de lo contrario la sintaxis estaria incorrecta y causaria una salida erronea
![](https://i.postimg.cc/s24ZHHWT/imagen-2023-12-27-162421903.png)
![](https://i.postimg.cc/tTmJ8K4N/imagen-2023-12-27-162452887.png)


# Comando `grep`

`grep` significa <u>**(Global Regular Expression Print)**</u>.

Utiliza **expresiones regulares** para realizar búsquedas en archivos.

**Sintaxis:** `grep [ExpresiónRegular] [archivoDondeBuscar]`

## Uso de `grep` con opciones

### Ignorar </u>Case Sensitive </u> `(-i)`
Buscará independientemente de si la letra o palabra a consultar es mayúscula o minúscula.
```bash
grep -i Action movies.csv
```
### <u>Contar Ocurrencias</u> `(-c)`
Saber cuántas veces se repite una palabra
```bash
grep -c Drama movies.csv # Mostrara el número de veces que se repite
grep -ic Drama movies.csv # Mostrara el número de veces que se repite pero con case senstive
```
### <u>Excluir Expresión</u> `(-v)`
Saber cuáles son los resultados que NO coinciden con la expresión regular
bash
```bash
grep -cv Drama movies.csv # Mostrara el número de veces que no aparece la palabra
```
### <u>Limitar Búsqueda</u> `(-m)`
Se puede limitar la búsqueda en líneas con la opción `-m` seguida del **número de líneas** que queremos encontrar.
```bash
grep -m 10 Fan movies.csv # Mostrara los 10 primeras líneas 
grep -vim 10 towers movies.csv # Permite incorporar mas expresiones y obtener una salida mas precisa
```
## Utilidad del comando grep
1. Buscar algún paquete en específico que tengas instalado:

    ```powershell
    dpkg --get-selections | grep nombreDelPaquete
    # dpkg --get-selections te dirá todos tus paquetes instalados
    # grep filtrará esa lista con el paquete que te interesa
    ```

2. Filtrar algún archivo en específico después de un `ls`:

    ```bash
    ls -al | grep myFile.txt

    # ls te dará la lista de todos tus archivos
    # grep filtrará todos y te mostrará únicamente el que deseas
    ```

3. Buscar algún contenido en específico dentro de algún archivo:

    ```bash
    cat unArchivoLargo.txt | grep "La línea que busco"

    # cat Te listará todo el contenido de ese archivo
    # grep te filtrará únicamente lo que quieres ver
    ```

4. Buscar una línea en específico en diferentes archivos por medio de un patrón:

    ```bash
    grep "string" archivo_*

    # grep buscará la palabra "string" en todos los archivos que comienzen por "archivo_" y te los mostrará.
    ```

5. Buscar usando expresiones regulares

    **Ejemplo:**Tienes un archivo llamado `test.txt` y adentro contiene la siguiente frase: **"Imagina que quieres buscar algo"**
    Entonces, podemos usar grep así:
    ```bash
    grep "Imagina .* algo" test.txt
    ```
    grep buscará alguna coincidencia, la expresion .* indica que ahí dentro puede haber una o más letras, cualquier que sea, así que podrías leerla como: **Imagina <u>(cualquier cosa)</u> algo**.
    Esto encontrará justo la frase que quieres:
    ```bash
    Imagina que quieres buscar algo
    ```

## Comando <u>World Count</u> `(wd)`
Uso del comando wc para contar palabras, caracteres y líneas en un archivo.
```bash
wc [archivo] # Muestra palabras, caracteres y líneas del archivo
wc -l [archivo]  # Número de líneas
wc -w [archivo]  # Número de palabras
wc -c [archivo]  # Número de caracteres
```


