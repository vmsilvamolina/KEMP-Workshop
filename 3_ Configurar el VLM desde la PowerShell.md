# Configurar el VLM desde la PowerShell

KEMP ofrece un módulo de administración para PowerShell. Para acceder a éste módulo es necesario acceder al siguiente enlace:

[LoadMaster Powershell API Wrapper](https://kemptechnologies.com/files/packages/current/KEMP.LoadBalancer.Powershell.zip)

## Importar el módulo en PowerShell

a)Primero debemos descomprimir el archivo descargado y guardarlo en una ruta que podamos acceder fácilmente.

b)Ejecutar una consola de PowerShell como administrador y correr los siguientes comandos:

    cd .\<Ruta donde se encuentra el módulo>
    Import-Module .\Kemp.LoadBalancer.Powershell.psd1

c) Para comprobar que el módulo se importó correctamente, ejecutamos:

    Get-Module

d) En caso de querer ver todos los comandos que trae el módulo es necesario ejecutar:

    Get-Command

e) Si necesitamos obtener ayuda sobre agún comando en particular, para conocer la sintaxis o ejemplos de uso, debemos ejecutar:

    Get-Help <comando>

## Crear un Virtual Service

a) El comando para crear un Virtual Service es:

    New-AdcVirtualService -Port <puerto> -Protocol tcp -VirtualService <IP del VS>

## Agregar un Real Server

b) 

    New-AdcRealServer -Port <puerto> -Protocol tcp -RealServer <IP del RS> -RealServerPort <puerto> -VirtualService <IP del VS>

