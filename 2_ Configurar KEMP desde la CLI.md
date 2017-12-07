# 

##

## Agregar un Real Server a un Virtual Service

a) Ejecutamos **show** para ver todos los Virtual Services configurados en el KEMP.
b) Para acceder al VS a editar debemos ejecutar **vip <IP del VS>**.
c) Si la intención es agregar otro servidor (Real Server), es requerido ejecutar **add <IP del nuevo RS>**.
d) Debemos ejecutar **exit** para guardar el cambio de forma parcial.
e) Al ejecutar **show** dentro de la ubicación actual vamos a observar el nuevo Real Server dentro del Virtual Service.
f) Y por último, para guardar todo el cambio, ejecutamos **exit**
