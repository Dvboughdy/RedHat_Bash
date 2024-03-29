
# Topic 1: ¿Como funciona el sistema de carpetas?
La carpeta con el símbolo **“/”** es la raíz, ahí es donde comienza todo el sistema de ficheros (el equivalente en Windows podría ser el fichero “C:\”). Dentro de esta carpeta hay varios ficheros, el que nos importa en este momento es el “Home”.

La carpeta **“Home”** contiene una carpeta por cada usuario del sistema y ya dentro de cada una de estas carpetas, estarán las carpetas que conocemos de toda la vida como imágenes, documentos, música, etc.

# Topic 2: ¿Cómo entender la información de la terminal?
Cuando abrimos la terminal vamos a ver algo como esto:
```bash
miguelangel@DESKTOP-3R804MK:~$
```
- **miguelangel** es el nombre del usuario que está activo. En tu caso aparecerá el nombre del usuario que esté activo en tu computadora.
- **DESKTOP-3R804MK** es el nombre que el sistema operativo le dio a la computadora. En este caso se usa Windows y ese es el nombre que en la instalación Windows le asignó al dispositivo. Si usas Linux aparecerá el nombre del PC que hayas colocado en la instalación.
- **~** es la carpeta en la que te encuentras y ahora es cuando empiezan las confusiones porque en el esquema no estaba una carpeta con ese símbolo. Más adelante verás como todo tiene sentido.
- Por último, **$** significa que somos un usuario normal y no un root o un superusuario. Más adelante hablaremos más acerca de esto.

# Topic 3: Comandos de la terminal
## 1. Comando "Print Working Directory" (`pwd`)
El comando **pwd** (Print Working Directory) muestra la ubicación actual en la jerarquía de carpetas. Al ejecutarlo, se obtiene la ruta completa del directorio actual, por ejemplo:
```bash
/home/miguelangel
```
Este comando es esencial para conocer la posición dentro del sistema de archivos.

## 2. Comando "Change Directory" (`cd`)
El comando **cd** (Change Directory) se utiliza para moverse entre carpetas sin salir de la terminal. Para cambiar a una carpeta específica, se escribe cd seguido del nombre de la carpeta, como en el siguiente ejemplo: actual, por ejemplo:
```bash
$ cd Documents
```
La terminal reflejará el cambio de directorio:
```bash
miguelangel@DESKTOP-3R804MK:~/Documents$
```

## 3. Comando `ls` - "Listar Contenido de Carpetas"
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

### 3.1 Funciones Adicionales del Comando `ls`
El comando ls es fundamental para explorar el contenido de directorios. Aquí se detallan algunas funciones adicionales y opciones útiles:

- **ls -a:** Lista todos los archivos, incluyendo los ocultos que comienzan con punto (.).
- **ls -A:** Lista todos los archivos en los directorios, excepto los ocultos.
- **ls -F:** Indica el tipo de elemento: / para directorios, * para ejecutables, @ para enlaces simbólicos, etc.
- **ls -h:** Muestra el tamaño en un formato legible para humanos.
- **ls -l:** Proporciona información detallada en formato largo.
- **ls -S:** Clasifica los contenidos por tamaño, con los archivos más grandes primero.
- **ls -R:** Lista recursivamente los subdirectorios encontrados.
- **ls -t:** Ordena por fecha de última modificación.
- **ls -u:** Ordena por fecha de último acceso.
- **ls -x:** Presenta los archivos en columnas.
- **ls -i:** Precede la salida con el número de i-node.

### 3.2 Ejemplos del comando `ls`:
- **ls -lt:** Muestra los archivos del más actual al más antiguo.
- **ls -ltr:** Muestra los archivos del más antiguo al más actual.
- **ls -lh:** Muestra el tamaño de los archivos de forma legible.
- **ls -lhS:** Muestra archivos ordenados por tamaño.
- **ls -la:** Muestra atributos de archivos y archivos ocultos.


## 4. Comando `file`
El comando **file** se utiliza para determinar el tipo de un archivo. Proporciona información sobre si un elemento es un archivo, un directorio, un enlace simbólico, etc. Ejemplo:

**file nombre_elemento:** Muestra información sobre el tipo de elemento, como archivo, directorio o enlace simbólico.
```bash
$ file curso-mongo-intro/.gitignore
descripción
```

# Topic 4: Atajos de la terminal
## Virgulilla (`~`)
La virgulilla (~) representa la carpeta del usuario en el directorio Home. Para regresar rápidamente al Home, se utiliza:
```bash
cd ~
```

## 1. Punto y Doble Punto (`.`) (`..`)
- **cd ..** Retrocede a la carpeta anterior.
- **cd ./miguelangel/Documents/:** Accede a una ruta más precisa.

## 2. Volver al Raíz Directamente con` cd ../..`
Para volver directamente a la raíz del sistema en un solo atajo:
```bash
cd ../..
```

## 3. Retornar a una Dirección Previa con `pwd` y `cd`

### 3.1 Primer modo:
Al ver la ruta actual con `pwd`, como por ejemplo:

```bash
/usuario/.nvm/.git.
```
Se puede regresar al Home o a otra carpeta anterior utilizando cd seguido de la dirección previa:
```bash
cd .nvm/.git
```

### 3.2 Segundo modo:
Retornar a una Dirección Previa con el Comando cd ~
El comando **cd -** permite regresar a la ruta previa en la que se estaba.

## 4. Slash (`/`)
El atajo slash (/) lleva directamente a la raíz donde se encuentran todas las carpetas del sistema operativo:

```bash
cd /
```

## 5. Atajos de Teclado para la Terminal
- **CTRL-C:** Termina el proceso de un comando en la terminal.

- **CTRL-D:** Termina la entrada de un comando.
- **CTRL-A:** Avanza al inicio de la línea.
- **CTRL-E:** Avanza al final de la línea.
- **CTRL-L:** Limpia la pantalla de la terminal.
- **TAB:** Autocompleta la ruta o el nombre del documento al que se quiere acceder.

# Topic 5: Manipulación de archivos y directorios
## 1. Creación de Directorios (`mkdir`)
El comando mkdir (Make Directory) se utiliza para crear directorios en la terminal. Ejemplos:
```bash
mkdir DirectorioInteresante: #Crea un directorio llamado "DirectorioInteresante".
mkdir DirectorioInteresante SecretosDeEstado # Crea varios directorios al mismo tiempo.
```

## 2. Creación de Archivos (`touch`)
El comando touch se emplea para crear archivos en la terminal. Ejemplo:
```bash
touch Secreto1 Secreto2 SecretoSecretario: #Crea varios archivos llamados "Secreto1", "Secreto2" y "SecretoSecretario".
```

## 3. Visualización de Directorios en Forma de Árbol (`tree -L`)
El comando tree muestra de manera jerárquica la estructura de directorios y archivos. Para instalarlo y usarlo:
```bash
sudo apt-get install tree  # Instalación
tree --version             # Verificar la versión
tree                       # Visualización básica
tree -L 2 # de longitud       # Visualización con longitud específica
```

## 4. Copia de Archivos (`cp`)
El comando cp (Copy) se utiliza para copiar archivos. Ejemplo:
```bash
cp nombreDelArchivoParaCopiar nombreParaLaCopia # Copia el archivo especificado con el nombre de la copia.
```

## 5. Movimiento y Renombrado de Archivos (`mv`)
El comando mv (Move) se emplea para mover y renombrar archivos. Ejemplos:
```bash
mv [archivoParaMover] [destinoDelArchivo] # Mueve el archivo al destino especificado.

## EJEMPLO
mv SecretoQueSeHizoPublico ../SecretosPublicos/ # Renombra el archivo.
```

## 6. Eliminación de Archivos (`rm`)
El comando `rm` **(Remove)** se utiliza para eliminar archivos. Ejemplo:
```bash
rm [nombreDelArchivoParaEliminar]: # Elimina el archivo especificado.
rm -r SecretoQueNadieDebeVer # Eliminar directorio con el flag -r
```

### 6.1 Opciones útiles de `rm`
- `-i` (de interactive) te pregunta si estás seguro de eliminar el archivo
- `-r` (de recursive) elimina todo lo que esté dentro de una carpeta
- `-f` (de force) fuerza a borrar todo.
  
>[!IMPORTANT]
>
> La opción `-f` se usa cuando no puedes borrar algún archivo, bien sea porque algo lo está usando o porque se está ejecutando.

# Topic 6: Visualización del contenido de los archivos

## 1. Comandos de Visualización Rápida: `head`, `tail`, y `cat`

- `head`: Muestra las primeras 10 líneas de un archivo.
- `tail`: Muestra las últimas 10 líneas de un archivo.
- `cat`: Muestra todo el contenido de un archivo de texto.

Ejemplos:
```bash
head proyecto.html -n 20 # Muestra las primeras 20 líneas del archivo "proyecto.html".
tail proyecto.html -n 20 # Muestra las últimas 20 líneas del archivo "proyecto.html".
```

## 2. Visualización Completa con `less`
```bash
less [nombreDelArchivoParaAbrir]: Abre el archivo en una interfaz que permite navegar y buscar.
```
### Uso de less:
Usa las flechas y el scroll para moverte.
- Presiona **"/"** para buscar palabras dentro del documento.
- Presiona **"q"** para salir de la interfaz.

## 3. Apertura en Programa Predeterminado con `xdg-open` o `code .` en (WSL)
- `xdg-open [archivoParaAbrir]`:  Abre el archivo en el programa predeterminado.
- `code [nombreDelArchivo]`**(WSL)**: Abre un archivo en Visual Studio Code.

### 3.1 Instalación de Dependencia (si es necesario):
```bash
sudo apt install xdg-utils
```
- **Ejemplo con xdg**:
```bash
xdg-open ejemplo.html: # Abre "ejemplo.html" en el programa predeterminado.
```

- **Ejemplo con code en (WSL)**:
```bash
code ejemplo.html . # Abre "ejemplo.html" en Visual Studio Code desde WSL.
```

## 4. Apertura de Carpeta con `nautilus` o `explorer.exe .` (WSL)
- **nautilus [nombreDeLaCarpeta]**: Abre la carpeta en Nautilus. (Funciona igual que xdg-open)
- **explorer.exe . (WSL)**: Abre la carpeta actual en el explorador de archivos de windows.

- **Ejemplo**:
```bash
nautilus CarpetaImportante # Abre la carpeta "CarpetaImportante" en Nautilus.
```

- **Ejemplo (WSL)**:
```bash
explorer.exe .: # Abre la carpeta actual en el explorador de archivos desde WSL.
```
## 5. Alternativa a las anteriores opciones con **`wslview`**
Tambien se puede usar los comandos
- `wslview ejemplo.tipoArchivo` ( abrir un archivo )
- `wslview nombreDirectorio` ( abrir un directorio )

Para ello es necesario utilizar el comando **`sudo apt install wslu` para instarlo y posteriormente usarlo**

Ejemplos:
```bash
wslview readme.md # abre el archivo en VSC
wslview index.html  #  abre eI archivo en eI navegador pordefecto
code index.html # abre el archivo en VSC' '
```
>[!NOTE]
>
> Estos comandos facilitan la visualización y apertura de archivos y carpetas desde la terminal, brindando flexibilidad y eficiencia en la gestión de archivos.
