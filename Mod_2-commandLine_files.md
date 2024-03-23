<div align="center">

# Línea de Comando y Archivos

</div>


# Capítulo 2: Acceder a la línea de comando

## 1. `La Bash Shell`
La línea de comandos de Linux, proporcionada por un programa llamado shell, permite ingresar instrucciones a un sistema informático. Red Hat recomienda usar el shell predeterminado, el GNU Bourne-Again Shell `(bash)`, para la administración del sistema.

Bash, una versión mejorada del Bourne Shell original en los sistemas UNIX, muestra un indicador de `shell` cuando espera la entrada del usuario.

- El indicador cambia de un carácter de dólar `($)`
```sh
[user@host ~]$
```

- A una almohadilla `(#)` cuando el shell se ejecuta como superusuario, root.
```sh
[user@host ~]#
```

> [!NOTE]
>
> **El shell de bash es conceptualmente similar al intérprete de línea de comandos cmd.exe de Microsoft Windows**. Sin embargo, bash tiene un lenguaje de scripting sofisticado y es más similar a Windows PowerShell. 
> 
> - En macOS, el shell predeterminado cambió a zsh a partir de macOS 10.15 Catalina.

### 1.1. <u>`Estructura de un comando en la shell`</u>
<div style="">
<ol>
  <li style="color:#40e0d0;">El comando a ejecutar</li>

  <li style="color:#40e0d0;">Las opciones para ajustar su comportamiento</li>

  <li style="color:#40e0d0;">Los argumentos que son los objetivos del comando</li>
</ol>
</div>

### 1.2. <u>`Iniciar sesión en un sistema local`</u>

Una terminal proporciona una interfaz basada en texto para ingresar comandos y ver la salida en un sistema informático. Para ejecutar el shell, es necesario iniciar sesión en la computadora a través de una terminal.

La consola física de una máquina Linux puede admitir múltiples consolas virtuales, cada una con su propia sesión de inicio de sesión independiente. Esto permite cambiar entre diferentes sesiones presionando **`Ctrl+Alt`** y una tecla de función **`(F1-F6)`**.

En Red Hat Enterprise Linux 9, la pantalla de inicio de sesión gráfica se ejecuta en la primera consola virtual `(tty1)`, con cinco consolas de texto adicionales disponibles `(tty2 - tty6)`. El entorno gráfico comienza en la primera consola virtual no utilizada por una sesión de inicio de sesión.

> [!NOTE]
>
> **Muchos administradores de sistemas optan por no ejecutar un entorno gráfico en sus servidores porque los usuarios no inician sesión en los servidores como un espacio de trabajo de escritorio.** La carga de trabajo de un servidor puede utilizar de forma más eficaz los importantes recursos que utiliza un entorno gráfico.

Los servidores sin cabeza, que no tienen teclado ni pantalla conectados, pueden proporcionar un indicador de inicio de sesión a través de su consola serial. Esto es útil para acceder al servidor si la conexión de red convencional no está disponible.

Sin embargo, en algunos casos se puede acceder a los servidores sin cabeza por otros medios a través de la red, por ejemplo, utilizando Virtual Network Computing (VNC) para ejecutar una interfaz gráfica en la máquina de destino.

### 1.3. `Iniciar sesión en un sistema remoto`

Acceder a un sistema remoto en Linux es común para usuarios y administradores, especialmente en entornos con servidores sin cabeza o en la nube. **La forma más común de acceder es a través de "Secure Shell" `(SSH)`, que cifra la conexión para garantizar seguridad.**

- **Ejemplo**
  - En este ejemplo, un usuario con un indicador de shell en la máquina `host` usa `ssh` para iniciar sesión en el `host remoto` del sistema Linux remoto como usuario `usuarioremoto`:

  ```sh
  [user@host ~]$ ssh remoteuser@remotehost remoteuser@remotehost's password: password [remoteuser@remotehost ~]$
  ```
**SSH permite la autenticación mediante contraseña o mediante claves públicas, siendo esta última más segura.** Con claves públicas, los usuarios tienen un archivo de identidad con una clave privada que corresponde a una clave pública configurada en el servidor.

- **Ejemplo**
  - En el siguiente ejemplo, un usuario con un símbolo del shell en la máquina `host` inicia sesión en el `host remoto` como `usuario remoto` con `ssh`, utilizando el método de autenticación de clave pública. La opción `-i` del comando `ssh` se utiliza para especificar el archivo de clave privada del usuario, que es `mylab.pem`. La clave pública coincidente ya está configurada como clave autorizada en la cuenta del `usuario remoto`.

  ```sh
  [user@host ~]$ ssh -i mylab.pem remoteuser@remotehost 
  The authenticity of host 'remotehost (192.0.2.42)' can't be established. ECDSA key fingerprint is 47:bf:82:cd:fa:68:06:ee:d8:83:03:1a:bb:29:14:a3. Are you sure you want to continue connecting (yes/no)? yes
  [remoteuser@remotehost ~]$
  ```


> [!IMPORTANT]
> 
> **Al utilizar SSH por primera vez en un nuevo sistema, se emite una advertencia de autenticidad del host.** Si se acepta, la clave del host remoto se guarda para futuras conexiones, protegiendo contra ataques de interceptación.

```sh 
[user@host ~]$ ssh remoteuser@remotehost remoteuser@remotehost's password: password [remoteuser@remotehost ~]$
```

**La gestión de claves privadas y la configuración de `SSH` son tareas esenciales para la seguridad en la conexión remota**. Es fundamental comprender cómo funcionan y cómo configurarlas adecuadamente para mantener la integridad de la conexión.


## 2. `Practica de modificación de contraseña de usuario desde la shell`

1. Inicia sesión en la estación de trabajo como `student` con la contraseña `"student"`. 

2. Accede a la ``shell`` o `terminal` y cambia la contraseña del usuario `"student"` de `"student"` a `"55TurnK3y"`.
```sh
[student@workstation ~]$ passwd
Changing password for user student.
Current password: student
New password: 55TurnK3y
Retype new password: 55TurnK3y
passwd: all authentication tokens updated successfully.
```

3. Cierra sesión **(Log out)** y vuelve a iniciarla como `student` con la nueva contraseña para verificar el cambio.

4. Bloquea y desbloquea la pantalla para confirmar que el nuevo inicio de sesión funciona correctamente.

5. Practica cómo apagar la estación de trabajo desde la interfaz con la opción gráfica en la opción `Power Off`, pero cancela la operación para no apagar el sistema.

6. Ejecuta un script al final del ejercicio, **es decir finalizar el laboratorio**, para asegurarte de que la contraseña del usuario `"student"` se restablezca correctamente.


## 3. `Ejecutar Comandos con Bash Shell`
En esta sección se abordaron varios comandos vistos en el curso previo de Linea de comandos
- `whoami`: Muestra el nombre del usuario actual.

- `date`: Muestra la fecha y hora actuales. 
	- Se puede personalizar utilizando el argumento más (+) y especificando una cadena de formato como lo es la hora (`+%R`) o la fecha (`+%x`).
- `passwd`: Permite cambiar la contraseña del usuario actual. Puede ser usado por el superusuario para cambiar la contraseña de otros usuarios.

- `file`: Determina el tipo de un archivo escaneando su encabezado compilado.

- `cat`: Muestra el contenido de archivos en la salida estándar. Se usa comúnmente para crear, ver o concatenar archivos.

- `less`: Permite visualizar archivos de texto uno a la vez, facilitando la navegación en archivos largos.

- `head`: Muestra las primeras líneas de un archivo. Por defecto, muestra las primeras 10 líneas.

- `tail`: Muestra las últimas líneas de un archivo. Por defecto, muestra las últimas 10 líneas.
	- Estos tambien permiten filtrar la cantidad de lineas que se deseen visualizar mediante el flag `-n num`

- `wc`: Cuenta líneas, palabras y caracteres en un archivo. Puede ser usado con opciones como `-l` (líneas), `-w` (palabras) y `-c` (caracteres).

- `Tabulación (Tab)`: Completa rápidamente comandos o nombres de archivos escribiendo suficiente para hacerlo único y luego presionando **Tab**.

- `useradd`: Comando para crear usuarios en el sistema. Puede tener muchas opciones que pueden ser completadas usando la función de tabulación.

- `Carácter de escape ()`: Permite escribir comandos en múltiples líneas para mejorar la legibilidad.

- `history`: Muestra una lista de comandos ejecutados anteriormente. Puede ser usado junto con el signo de exclamación `(!)` para expandir comandos anteriores sin volver a escribirlos.

- `Teclas de flecha y combinaciones de teclas`: Ayudan a navegar y editar comandos anteriores en el historial del shell, como las teclas de flecha para navegar y `Esc +` . o `Alt +` . para insertar la última palabra del comando anterior.

### 3.1. `Atajos útiles de edición de línea de comandos`

<p align="center">
  <img src="https://i.postimg.cc/Zq3jC8ts/Screenshot-2024-03-22-220209.png" alt="Aquí va el texto del enlace">
</p>

# Capítulo 3: Administrar archivos desde la línea de comandos




# Capítulo 4: Obtener ayuda en Red Hat Enterprise Linux




# Capítulo 5: Crear, ver y editar archivos de texto
