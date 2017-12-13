# Configurar el VLM desde la CLI 

## Agregar un Virtual Service

a) Ejecutamos **show** para ver todos los Virtual Services configurados en el KEMP.
b) Desde el CLI de administración ejecutamos **vip <IP del nuevo Virtual Service>** para crear un VS nuevo.
c) Con el comando **show** vemos los Virtual Service ya creados.
    c.1) En caso de querer observar la configuración de un VS en particular, se debe ejecutar **show <IP del VS>**.

## Agregar un Real Server a un Virtual Service

d) Si la intención es agregar un servidor (Real Server), es requerido ejecutar **add <IP del nuevo RS>**.
e) Debemos ejecutar **exit** para guardar el cambio de forma parcial.
f) Al ejecutar **show** dentro de la ubicación actual vamos a observar el nuevo Real Server dentro del Virtual Service.
g) Y por último, para guardar todo el cambio, ejecutamos **exit**.

## Modificar el puerto del Virtual Service

Para modificar el puerto del Virtual Service es necesario, editar la configuración del mismo:

a) vip <IP del VS a modificar>
b) port <Ej: 443>
c) exit
d) show <IP del VS>

## Modificar el puerto del Real Server

e) vip <IP del VS a modificar>
f) server <IP del Real Server>
g) port <Ej: 443>
h) exit
i) exit
j) show <IP del VS>