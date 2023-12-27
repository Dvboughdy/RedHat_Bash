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


### Control de los permisos 
- **+ (`Agrega un permiso`)**.
- **- (`Elimina un permiso`)**.
- **= (`Asigna permisos específicos`)**.
  