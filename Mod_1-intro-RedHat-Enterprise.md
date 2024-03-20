<div align="center">

# Introducción a Red Hat Enterprise Linux #

</div>

# Capítulo 1: Introducción a Red Hat Enterprise Linux


 ## 1. `¿Por qué deberias aprender Linux?`
- Es una tecnologia fundamental en los profesionales de TI
- Gestiona los sistemas de punto de venta y mercados bursatiles del mundo
- Ejecuta al mayoria de las 500 supercomputadoras más importantes del mundo
- Se esta expandiendo en el uso de espacios empresariales 


## 2. `¿Que hace que Linux sea genial?`
- Es de codigo abierto
- proporciona una interfaz de linea de comandos (CLI) para un facil acceso y una potente creación de comandos
- Es un modular Sistema operativo que está diseñado para reemplazar o quitar componentes fácilmente.

## 3. `¿Qué es el software de código abierto?`
- Es un software con código fuente que cualquiera puede usar, estudiar, modificar y compartir
- Las licencias de codigo abierto promueven la colaboración, el intercambio, la transparencia y la innovación rapida, ya que animan a más personas a modificar y mejorar el software
- estos software se pueden proporcionar para uso comercial 
-Algunas licencias permiten reutilizar el codigo en productos propietarios 

### 3.1. <u>`Beneficios para el usuario`</u>
<div style="">
<li style="color:#40e0d0;"> Control</li>
<p>Permite ver lo que hace el codigo y mejorarlo</p>

<li style="color:#40e0d0;" >Adiestramiento</li>
<p>Permite aprender del codigo del mundo real y desarrollar más aplicaciones que sean utiles</p>

<li style="color:#40e0d0;" >Seguridad</li>
<p>Ayuda a inspeccionar el codigo confidencial y asi mismo corregirlo sin la ayuda de los desarrolladores originales</p>

<li style="color:#40e0d0;" >Estabildiad</li>
<p>El codigo puede sobrevivir a la pérdida del desarrollador original</p>
</div>

### 3.2. <u>`Tipos de licencias de código abierto`</u>

<li style="color:#40e0d0;" >Copyleft</li>

- Estas licencias estan iseñadas para fomentar el mantenimiento del codigo abierto

- Deben permitir la libertad de que otros puedan copiar, cambiar y distribuir el codigo
- Ayudan a mantener abierto el codigo existente y las mejoras a ese código y aumentan la cantidad de código abierto disponible
- Las licencias copyleft más comunes incluyen la Licencia Pública General GNU (GPL) y la Licencia Pública GNU Menor (LGPL)

<li style="color:#40e0d0;" >Permisivo</li>

- Estan diseñadas para maximizar la reutilización del código

- Puede usar el código fuente para cualquier proposito siempre y cuando se conserven las declaraciones de derechos de autor y licencia
- las licencias permisivas facilitan la reutilización del código,pero corren el riesgo de fomentar mejoras exclusivas de los propietarios.
- Ejemplos de licencias permisivas incluyen la licencia MIT/X11, la licencia BSD simplificada y la licencia de software Apache 2.0.

> [!NOTE]
> Hoy en día, la mayoría de los desarrolladores de código abierto trabajan para organizaciones que les pagan para que participen en proyectos de código abierto para construir y contribuir con las mejoras que la organización y sus clientes necesitan.

## 4. `¿Qué es una distribución de Linux?`
Es un sistema operativo instalable que se construye apartir de un kernel de linux y admite programas y biblotecas de usuario.

- En 1991, Linus Torvalds desarrollo un kernel similar a UNIX al que llamo Linux

-El kernel de linux se complementa con otro software de código abierto, incluyendo utilidades y programas del Proyecto GNU, una interfaz grafia del MIT

- Tambien incluye un servidor de correo llamada sendemail y el servidor web HTTP

> [!NOTE]
> **<u>El kernel es el nucleo del sistema operativo</u> y administra el hardware, la memoria y la programación de los programas en ejecución.**

### 4.1. <u>`Caracteristicas de las distribuciones de Linux`</u>

- Las distribuciones consisten en un kernel de Linux y soportan programas de espacio de usuario.

- Las distribuciones pueden ser pequeñas y de un solo propósito, o pueden incluir miles de programas de código abierto.

- Las distribuciones proporcionan un medio para instalar y actualizar el software y sus componentes.

-   El proveedor de distribución da soporte al software e, idealmente, participa en la comunidad de desarrollo. 

## 5. `¿Quién es Red Hat?`
Es el provedor mundial de soluciones de software de código abierto, mediante el uso de enfoque impulsado por la comunidad para tecnologias confiables y de alto rendimiento en la nube, Linux, middleware, almacenamiento y virtualización.

> [!NOTE]
> 
> **<u>Middleware</u> es un software que conecta aplicaciones o componentes en una red distribuida.** Facilita la comunicación entre sistemas que no están diseñados para conectarse directamente 

- Cumplen el papel de conectar a losclientes con la comunidad de código abierto

- Es conocido por su participación en la comunidad Linux y la distribución de Red Hat Enterprise Linux `(RHEL)`.

- Participa activamente en proyectos de comido abierto como lo son middleware, tecnologias de la nube como **OpenStack** y **OpenShift**, y los proyectos de almacenamiento basados en software **Ceph** y **Gluste**

## 6. `Red Hat Enterprise Linux Ecosystem`

**Red Hat Enterprise Linux** `(RHEL)` es una distribución comercial de Linux de grado de producción de Red Hat. **Se desarrolla e integra software de código abierto en RHEL a través de un proceso de múltiples etapas.**

- **<u>Participa activamente</u>** en el apoyo a proyectos individuales de código abierto, contribuyendo con código, tiempo de desarrollo, recursos y soporte. También colabora estrechamente con desarrolladores de otras distribuciones Linux para la calidad general del software.
  
- **<u>Patrocina</u>** y **<u>fusiona</u>** proyectos de código abierto en la distribución de Fedora impulsada por la comunidad, proporcionando un entorno de trabajo gratuito para el desarrollo y la prueba de características que luego se incorporan a CentOS Stream y los productos RHEL.

- **<u>Estabiliza</u>** el software de CentOS Stream para estar listo para el soporte a largo plazo y la estandarización, e lo integra en RHEL, la distribución lista para producción.

<p align="center">
  <img src="https://i.postimg.cc/sgJs4fYn/imagen-2024-03-20-155221670.png" alt="Aquí va el texto del enlace">
</p>


## 7. `Distribución de Fedora`
Fedora es un proyecto comunitario que produce y lanza un sistema operativo basado en Linux de forma gratuita y completa. Se prioriza la innovación y la excelencia por encima de la estabilidad a largo plazo.

### 7.1. <u>`Extra Packages for Enterprise Linux (EPEL)`</u>
`EPEL` es un repositorio de paquetes compatible con la comunidad de Fedora, que permite a los clientes de RHEL ejecutar cargas de trabajo con dependencias de software que no son compatibles con RHEL.

## 8. `CentOS Stream`
**CentOS Stream** es el proyecto de upstream para RHEL. Es una distribución de integración y entrega continua con compilaciones nocturnas probadas y estables.

> [!NOTE]
> 
> ***"upstream"* se refiere a la dirección en la que fluyen los cambios y mejoras originales antes de ser integrados en otras versiones derivadas o modificadas del proyecto.** *En el caso de CentOS Stream como el upstream para RHEL, significa que CentOS Stream es donde se desarrollan y prueban las nuevas features y updates*
> 
## 9. `Diferencias entre Fedora, CentOS Stream y RHEL`

<p align="center">
  <img src="https://i.postimg.cc/7YFjGFjK/imagen-2024-03-20-161801551.png" alt="Aquí va el texto del enlace">
</p>
## `Mas información adicional de RHEL`

### 6.1. <u>`RHEL for Edge`</u>
**RHEL for Edge** es una variante basada en imágenes de RHEL, con un mecanismo de implementación diferente. Ofrece capacidades de gestión segura y escalable.

### 6.2. <u>`Red Hat CoreOS`</u>
RHCOS es un host de contenedores RHEL basado en imágenes. Se integra en la Plataforma de Contenedores Red Hat OpenShift (RHOCP) para aplicaciones nativas de la nube.

### 6.3. <u>`Red Hat Universal Base Image (UBI)`</u>
UBI es una imagen base redistribuible de RHEL diseñada para casos de uso de aplicaciones en contenedores.

### 6.4. <u>`Red Hat Enterprise Linux Continuous Development`</u>
El desarrollo de RHEL comienza con la selección de la última versión de Fedora como base para la distribución continua de desarrollo CentOS Stream.

### 6.5. <u>`Obtaining Red Hat Enterprise Linux`</u>
RHEL se obtiene típicamente con una suscripción de soporte pagada. También hay formas de obtener RHEL y otros productos del ecosistema de RHEL, muchas sin costo.

#### => `Red Hat Developer Subscription`
**Red Hat proporciona una suscripción gratuita para desarrolladores a través del Programa para Desarrolladores de Red Hat**. Permite a los desarrolladores crear, probar y demostrar aplicaciones en el mismo software de Red Hat utilizado en los sistemas de producción.

### 6.6. <u>`Plataformas de Nube Pública`</u>
Los principales proveedores de nube pública como **Amazon Web Services, Google Cloud Platform y Microsoft Azure**, ofrecen imágenes oficiales de RHEL para implementar instancias de RHEL, con gestión de suscripciones a través del servicio Red Hat Cloud Access.

### 6.7. <u>`Contenedores`</u>
Se pueden utilizar imágenes base universal de Red Hat y contenido asociado para desarrollo e implementación sin una suscripción de Red Hat. Para obtener soporte operativo y acceso a herramientas no UBI, los contenedores deben implementarse en una plataforma compatible con Red Hat, como OpenShift o Red Hat Enterprise Linux. El acceso a contenido no UBI requiere una suscripción de Red Hat.