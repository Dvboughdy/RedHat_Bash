
# ¿Como funciona el sistema de carpetas?
La carpeta con el símbolo **“/”** es la raíz, ahí es donde comienza todo el sistema de ficheros (el equivalente en Windows podría ser el fichero “C:\”). Dentro de esta carpeta hay varios ficheros, el que nos importa en este momento es el “Home”.

La carpeta **“Home”** contiene una carpeta por cada usuario del sistema y ya dentro de cada una de estas carpetas, estarán las carpetas que conocemos de toda la vida como imágenes, documentos, música, etc.

# ¿Como funciona el sistema de carpetas?
Cuando abrimos la terminal vamos a ver algo como esto:
```bash
miguelangel@DESKTOP-3R804MK:~$
```
- **miguelangel** es el nombre del usuario que está activo. En tu caso aparecerá el nombre del usuario que esté activo en tu computadora.
- **DESKTOP-3R804MK** es el nombre que el sistema operativo le dio a la computadora. En este caso se usa Windows y ese es el nombre que en la instalación Windows le asignó al dispositivo. Si usas Linux aparecerá el nombre del PC que hayas colocado en la instalación.
- **~** es la carpeta en la que te encuentras y ahora es cuando empiezan las confusiones porque en el esquema no estaba una carpeta con ese símbolo. Más adelante verás como todo tiene sentido.
- Por último, **$** significa que somos un usuario normal y no un root o un superusuario. Más adelante hablaremos más acerca de esto.

# Comandos de la terminal
## Comando "Print Working Directory" (pwd)
El comando **pwd** (Print Working Directory) muestra la ubicación actual en la jerarquía de carpetas. Al ejecutarlo, se obtiene la ruta completa del directorio actual, por ejemplo:
```bash
/home/miguelangel
```
Este comando es esencial para conocer la posición dentro del sistema de archivos.

## Comando "Change Directory" (cd)
El comando **cd** (Change Directory) se utiliza para moverse entre carpetas sin salir de la terminal. Para cambiar a una carpeta específica, se escribe cd seguido del nombre de la carpeta, como en el siguiente ejemplo: actual, por ejemplo:
```bash
$ cd Documents
```
La terminal reflejará el cambio de directorio:
```bash
miguelangel@DESKTOP-3R804MK:~/Documents$
```

## Comando ls - Listar Contenido de Carpetas
El comando ls (List) es utilizado para conocer el contenido de las carpetas en la terminal. Aquí hay algunas variaciones y opciones importantes:

**ls:** Lista los archivos y carpetas en la ubicación actual.
Ejemplo de ls

**ls -l:** Proporciona información detallada, incluyendo permisos, tamaño, fecha de modificación, etc.
ls -l

**ls -lh:**: Proporciona información detallada con tamaños legibles para humanos.
ls -lh

**ls -R:** Muestra una lista de subdirectorios de cada directorio visible.

**ls -a:** Muestra listas de directorios ocultos.

**ls -al:** Combina las opciones -a y -l para mostrar información detallada de todos los archivos, incluyendo los ocultos.

## Comando file
El comando **file** se utiliza para determinar el tipo de un archivo. Proporciona información sobre si un elemento es un archivo, un directorio, un enlace simbólico, etc. Ejemplo:

**file nombre_elemento:** Muestra información sobre el tipo de elemento, como archivo, directorio o enlace simbólico.
```bash
$ file curso-mongo-intro/.gitignore
descripción
```
# Atajos de la terminal
## Virgulilla (~)
La virgulilla (~) representa la carpeta del usuario en el directorio Home. Para regresar rápidamente al Home, se utiliza:
```bash
cd ~
```
## Punto y Doble Punto (.) (…)
**cd ..:** Retrocede a la carpeta anterior.
**cd ./miguelangel/Documents/:** Accede a una ruta más precisa.
## Volver al Raíz Directamente con cd ../..
Para volver directamente a la raíz del sistema en un solo atajo:
```bash
cd ../..
```

## Retornar a una Dirección Previa con pwd y cd

### Primer modo:
Al ver la ruta actual con pwd, como por ejemplo: **/usuario/.nvm/.git.**
Se puede regresar al Home o a otra carpeta anterior utilizando cd seguido de la dirección previa:
```bash
cd .nvm/.git
```

### Segundo modo:
Retornar a una Dirección Previa con el Comando cd ~
El comando **cd -** permite regresar a la ruta previa en la que se estaba.

## Slash (/)
El atajo slash (/) lleva directamente a la raíz donde se encuentran todas las carpetas del sistema operativo:

```bash
cd /
```
## Atajos de Teclado para la Terminal
- **CTRL-C:** Termina el proceso de un comando en la terminal.

- **CTRL-D:** Termina la entrada de un comando.
- **CTRL-A:** Avanza al inicio de la línea.
- **CTRL-E:** Avanza al final de la línea.
- **CTRL-L:** Limpia la pantalla de la terminal.
- **TAB:** Autocompleta la ruta o el nombre del documento al que se quiere acceder.