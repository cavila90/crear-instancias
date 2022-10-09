### Arquitectura 2

Arquitectura para múltiples instancias de Odoo que consiste en una sóla base de datos en la misma red que múltiples instancias de Odoo.
En esta sección, vamos a parametrizar docker-compose.yaml. Es decir, los atributos de este archivo lo alojaremos en otro archivo llamado .env .

#### Orden de Ejecución
1. Crear red interna, de modo que los contenedores puedan ser localizados entre sí por sus nombres.
~~~
docker network create net-odoo
~~~
2. Levantar la base de datos, para esto, debe ejecutar el siguiente comando dentro del directorio db_postgres
~~~
docker-compose up -d
~~~
3. Levantar un proyecto, para esto, debe ejecutar el siguiente comando dentro del directorio proyecto_odoo_*
~~~
docker-compose up -d
~~~

#### Consideraciones
1. Solo levanta una vez el proyecto db_postgres
2. proyecto_odoo lo puedes replicar para tener varias instancias de Odoo. Debes tener en cuenta que los parámetros .env deben ser diferentes.
3. La presentación actual de todo los proyectos en un solo repositorio es para fines prácticos en la masterclass. Uselo solo como una plantilla.


#### Recomendaciones
1. Cada una de las carpetas proyecto_odoo_* representa a un proyecto que tiene una versión diferente de Odoo, configuraciones y módulos diferentes. Por lo que se recomienda que cada uno tenga su propio repositorio. 