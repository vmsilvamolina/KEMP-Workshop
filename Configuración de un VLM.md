# Configuración de un VLM

Para el primer laboratorio vamos a ver las buenas prácticas a la hora de configurar un VLM (Virtual LoadMaster). Antes de comenzar debemos de confirmar que contamos con todos los requisitos:

## Requisitos

* Notebook con software para virtualizar: Hyper-V, VirtualBox, VMware, KVM.
* Imagen del VLM Trial (para descargar [aquí](https://kemptechnologies.com/vlm-download/)).
* Acceso a internet para completar el proceso de activación de la licencia.

Ya con los requisitos reunidos, vamos a comenzar a detallar los pasos necesarios para completar el procedimiento necesario requerido para la configuración de nuestro balanceador.

## 1- Crear nuestro KEMP ID

Antes de comenzar a realizar cualquier otra tarea es necesario registrarse en el portal de KEMP para poder acceder a los recursos que se ofrecen, como guías, referencias de sizing y comparaciones, así como los trials ilimitados.

La URL para registrarse es:

[https://kemptechnologies.com/kemp-id-registration-resource-library/](https://kemptechnologies.com/kemp-id-registration-resource-library/)


## 2- Descargar el trial de VLM

a) Ya registrados en el portal de KEMP, vamos a navegar a ***Resources*** y luego en la sección *Trial* seleccionar ***Try LoadMaster***.

b) En la sección de la página donde especifica Virtual, seleccionamos ***Download***.

c) Al encontrarmos logueados en el portal, vamos a saltar directamente a las opciones de descarga. Para ello completamos los valores que nos indican:

* Hypervisor
* País

d) Y luego, habiendo aceptado el Acuerdo de Licencia con el Usuario Final, vamos a seleccionar Download para descargar nuestro Trial.


## 3- Generar la Máquina Virtual

> Para el resto del Workshop se va a tomar Hyper-V como solución de hypervisor

a) Desde la consola de Hyper-V, vamos a crear una nueva VM.

b) Dentro del wizard que aparece para generar una nueva VM, vamos a completar los siguientes campos:

* Nombre y ubicación de la VM.
* Generación (por defecto).
* Memoria (para el workshop con 2GB está correcto). Revisar que no quede marcado como dinámica.
* Networking vamos a dejarlo como aparece (desconectada).
* En virtual hard disk, seleccionar la opción que indica "Attach a virtual hard disk later".

Con la configuración anterior estamos en condiciones de finalizar el asistente de creación.

## 4- Redes

a) En caso que la notebook no tenga ya un vSwitch para brindar conectividad a las VMs, vamos a generar uno del tipo **Externo**.

b) Posteriormente, dentro de las propiedades de la VM, vamos a configurar que el adaptador se conecte a este vSwitch.

c) En caso de que el vSwitch no tenga DHCP, al momento de encender el VLM es necesario configurar una IP del rango.

## 5- Configuración inicial

a) Configurar la conectividad del VLM, definiendo la IP, máscara y GW

b) Cambiar la contraseña por defecto.

c) Agregar un usuario nuevo.

## 6- Agregar un Virtual Service

a) Agregar un Virtual Service y definir como Real Server el servidor con IIS

b) Definir en el archivo *hosts* una entrada que sea webserver y apunte a la IP del Virtual Service.

c) Acceder desde un navegador a http://webserver
