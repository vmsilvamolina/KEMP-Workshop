# Configurar High Availability

La alta disponibilidad proporciona un mecanismo que permite una continuidad del servicio.

Para ello es requerido contar con 2 balanceadores y que cumplan con lo siguiente:

* Los balanceadores debe estar ubicado en la misma subred (a menos de 100 metros y en el mismo lugar físico).
* Asegúrese de tener más de una interconexión entre los dos LoadMasters para evitar la pérdida de datos o la falta de disponibilidad.
* Los dos balanceadores deben usar la misma puerta de enlace predeterminada.
* Use Network Time Protocol (NTP) para mantener las horas en LoadMasters actualizadas.
* Asegúrese de que los switches no impidan el MAC spoofing.

## Configuración en el primer nodo

a) Iniciar sesión en el nodo que se requiere como *master*.
b) En el menú principal, seleccionar **System Configuration** y luego la opción de HA.
c) Dentro de la pantalla que aparece seleccionar **HA mode** y clic en confirmar.
d) Seleccionar **HA (First) Mode** y clic en Ok en la ventana que aparece.
e) Clic en Ok en la ventana que nos indica recordar la Shared IP.
f) En las opciones ingresar la **HA Shared IP Address** (IP para el servicio de HA). Para confirmarla, clic en Set Shared Address. Clic Ok.
g) El siguiente campo es **HA Partner IP address**, ingresar la IP del otro balanceador y luego clic en **Set Partner address**.
h) Definir un **HA Virtual ID** para identifiar el HA pair (debe ser único en la red).
i) Reiniciar el balanceador.

## Configuración en el segundo nodo

a) Iniciar sesión en el nodo que se requiere como *master*.
b) En el menú principal, seleccionar **System Configuration** y luego la opción de HA.
c) Dentro de la pantalla que aparece seleccionar **HA mode** y clic en confirmar.
d) Seleccionar **HA (second) Mode** y clic en Ok en la ventana que aparece.
e) Clic en Ok en la ventana que nos indica recordar la Shared IP.
f) En las opciones ingresar la **HA Shared IP Address** (IP para el servicio de HA). Para confirmarla, clic en Set Shared Address. Clic Ok.
g) El siguiente campo es **HA Partner IP address**, ingresar la IP del otro balanceador y luego clic en **Set Partner address**.
h) Definir un **HA Virtual ID** para identifiar el HA pair (definido anteriormente).
i) Reiniciar el balanceador.
