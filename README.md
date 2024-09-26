Para configurar Odoo con compose, primero hay que crearse los archivos docker-compose.yml y odoo.conf y escribir la configuracion. Después se crearán una serie de carpetas que acabaran asi:
-DockerCompose
    -config_odoo
        -odoo.conf
    -dev_addons
    -log
    -docker-compose-yml
    
Ahora con el PowerShell de windows hay que ir a la carpeta principal (DockerCompose) y ejecutar "docker-compose up -d" para que se ejecute la configuración

Para crear un módulo de Odoo, vamos al Docker y ejecutamos el contenedor "dockercompose". Ahora, en el contenedor "web-1" (dentro del contenedor "dockercompose") hay que darle a "Open in terminal" y ejecutar los siguientes comandos("dam" será el nombre del módulo): 
  -> cd mnt/extra-addons
  -> docker scaffold dam

Ahora iremos a DockerCompose/dev_addons/dam y descomentaremos unas cuantas lineas de codigo:
 -Del archivo models/models.py descomentaremos las lineas de la 3 a la 10
 -Del archivo _manifest_.py descomentaremos la linea 25
 -Del archivo views/views.xml descomentaremos las lineas:
     -> 5 a 15 (eliminando la linea 12: "<field name="value2"/>"): explicit list view definition
     -> 18 a 22: actions opening views on models
     -> 41: Top menu item
     -> 43: menu categories (Solo el primero)
     -> 49 y 50: actions (Solo el primero)
Ahora iremos al navegador y nos meteremos en la página "http://localhost:8069"
Al introducir nuestros datos y entrar a una base de datos de Odoo iremos a Ajustes y activaremos el modo de desarrollador
Ahora iremos a aplicaciones y buscaremos el modulo dam. Lo activaremos y ya podremos acceder a él en la esquina superior izquierda
