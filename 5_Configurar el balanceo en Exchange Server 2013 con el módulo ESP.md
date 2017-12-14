# Configurar el balanceo en Exchange Server 2013 con el módulo ESP

Para configurar el balanceo en Exchange Server 2013, existe dentro de los recursos que ofrece KEMP un template para descargar desde la web. El enlace de descarga es el siguiente:

[Microsoft Exchange 2013 ESP Template with LoadMaster 7.2.37.1 and later](http://kemptechnologies.com/files/assets/templates/Exchange2013ESP.tmpl)

### 1- Agregar el template a nuestro KEMP

a) Iniciar sesión en la IP configurada para la HA.

> Al tener ya nuestro laboratorio con los balanceadores en High Availability, vamos a trabajar desde la **Shared IP**.

b) Navegar en los menús siguientes: *Virtual Services* > *Manage Templates* y en la sección *Import Templates*, elegir el archivo a importa y luego clic en el botón *Add New Template*.

### 2- Generar el Virtual Services para los servicios de Exchange Server

a) Ir a la sección *View/Modify Services* dentro del menú *Virtual Services* y seleccionar el botón *Add New*.
b) En el campo Virtual Address definir la IP del VS. Por ejemplo 10.100.10.88.
c) En el campo Use Template, dentro de la lista desplegable seleccionar **Exchange 2013 HTTPS Offloaded with ESP**.
d) Clic en *Add this Virtual Service*.

### 3- Definir los Real Servers de nuestro servicio de Exchange

a) Al haber creado un Virtual Service ya nos encontramos ubicados para seleccionar un SubVS y editarlo seleccionando *Modify* en alguno de ellos.
b) Navegar a la sección *Real Servers*.
c) Seleccionar el botón *Add New...*.
d) En el campo *Real Server Address* definir la IP del servidor de Exchange al cual pretendemos balancear sus servicios.
e) Marcamos la opción *Add to all SubVSs*.
f) Clic en *Add This Real Server* para agregar éste servidor en todos los Sub Virtual Services.

> Repetir este proceso para todos los Real Server que se pretendan balancear.

### 4- Agregar el certificado al balanceador

a) Acceder a la opción *SSL Certificates*, que se encuentra dentro del menú *Certificates & Security*.
b) Seleccionar *Import Certificate*.
c) En la opción *Certificate File*, buscar el certificado a instalar. Clic en *Open*.
d) En el campo *Pass Phrase* ingresar el valor de la contraseña definida en el certificado.

### 5- Asignar el certificado al Virtual Service

a) Dentro de la ubicación en la que nos encontramos debido a la configuración anterior, vamos a identificar el certificado a instalar.
b) Seleccionar el Virtual Service al que pretendemos asignar el certificado en cuestión dentro de la lista *Available VS*, y asignarlo por medio del botón con el signo ">".
c) Clic en *Save Changes*.

### Definir el dominio para el inicio de sesión (Endpoint)

a) Primero acceder desde el menú *Certificates & Security* a la opción *LDAP Configuration*.
b) Dentro de la sección LDAP Endpoints, ingresar el nombre del dominio y luego clic en *Add new LDAP Endpoint*.
c) Completar el campo *LDAP Server(s)* con la IP del Domain Controller. Clic en *LDAP Server(s)* para guardar el valor.
d) El siguiente campo es *Admin User*, completar ingresando el usuario de dominio a utilizar para la configuración. Clic en *Set Admin User* para guardar el valor ingresado.
e) Como último campo a definir tenemos *Admin User Password*, en el que se debe definir la contraseña del usuario anteriomente seleccionado. Clic en *Set Admin User Password* para completar la configuración del endpoint.

### Definir el dominio para el inicio de sesión (Client SSO)

a) Acceder por medio del menú *Virtual Services* a la sección de configuración denominada *Manage SSO* (Single Sign On).
b) En *Client Side Single Sign On Configurations*, definir la configuración por medio del campo *Add new Client Side Configuration*. Para ello completar con el nombre de dominio y hacer clic en el botón *Add*.
c) De lo anterior surge un nuevo menú de opciones a completar. El primer valor es el *LDAP Endpoint*: seleccionar de la lista desplegable el definido anteriormente.
d) En el campo *Domain/Realm*, ingresar el valor de NetBIOS del dominio y luego clic en *Set Domain/Realm Name*.
e) Por último resta definir el usuario a utilizar como test. El campo es *Test User* y guardamos el cambio utilizando el botón *Set Test User*.
f) Ya definido el usuario, ingresamos la contraseña en el campo *Test User Password* y terminamos el procesos guardando el cambio con el botón *Set Test User Password*.

### Configuración de los Virtual Services

a) Dentro de cada SubVS vamos a ubicarnos en la sección *ESP Options* para comenzar a definir las opciones de autenticación.
b) En *Client Authentication Mode* seleccionar *Form Based*.
c) Dentro del campo *SSO Domain* seleccionar de la lista el dominio que definimos anteriormente.
d) Para el campo *Allowed Virtual Hosts*, se debe ingresar una exprepsión wildcard (*dominio) para el dominio en cuestión. Clic en *Set Allowed Virtual Hosts*.
e) El siguiente valor a modificar es *Server Authentication Mode*, que se debe definir como *Basic Authentication*. 

### Configuración de los servidores de Exchange

a) Iniciar sesión en el ECP (Exchange Control Panel) accediendo a la siguiente URL: https://ServerIP/ecp.
b) Navegar a Servidores > Directorios Virtuales.
c) Seleccionar OWA para editarlo.
d) En la sección autenticación, elegir la opción "Marcar uno o más métodos de autenticación estándar".
e) Corroborar que la configuración "Autenticación básica" sea la única marcada.
f) Guardar los cambios.
g) Iniciar sesión en el servidor de Exchange.
h) Abrir la consola  de IIS.
i) Reinciar el IIS.