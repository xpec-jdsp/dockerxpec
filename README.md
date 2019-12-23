# Estructura para Magento233 en docker
### Apache2 + Mysql + Varnish + Redis + Elasticsearch + Magento233 pre instalado

#### Apache2

Viene instalado apache2 con *php 7.1* con las librerias necesarias para el funcionamiento de *Magento 2.X*, el nombre predeterminado del contenedor es xpec_apache2, su configuracion esta contenida en la carpeta web_server, en la cual se encuentra una carpeta simbolica llamada *virtualhosts* donde esta ubicados los virtual host de los proyectos a implementar, puedes adaptar esta configuracion a tus necesidades antes de montar el docker.

*Nota:* si agregas un proyecto diferente al predeterminado revisar el _README.md_ contenido en */proyectos/*, y seguir las instrucciones antes de montar el docker para un correcto funcionamiento.

#### Mysql

Viene instalado Mysql version 5.7 con las configuraciones necesarias para el funcionamiento de *Magento 2.X* el nombre predeterminado del contenedor es xpec_mysql, su configuracion esta contenida en la carpeta database_server, en la cual se encuentra una carpeta simbolica llamada *db_import* donde se alojaran los sql a importar/exportar, dentro del container este _PATH_ puede ser accedido mediante la ruta */var/db_import/*.

*Nota:* Editar en el archivo *docker-compose.yml* el campo de la contraseña del Mysql.

#### Varnish

Viene instalado Varnish 3.0 con las configuraciones necesarias para el funcionamiento de *Magento 2.X*, el nombre predeterminado del contenedor es xpec_varnish, su configuracion esta contenida en la carpeta cache_server, en la cual se encuentra una carpeta el archivo *default.vcl* el cual es proveido por Magento con su configuracion recomendada.

#### Redis

Viene instalado Redis con las configuraciones necesarias para el funcionamiento de *Magento 2.X*, el nombre predeterminado del contenedor es xpec_redis, su configuracion esta contenida en la carpeta redis_server.

#### Elasticsearch

Viene instalado Elasticsearch version 6.4.2 con las configuraciones necesarias para el funcionamiento de *Magento 2.X*, el nombre predeterminado del contenedor es xpec_elasticsearch, se usa directamente la imagen de docker recomendada por Elastic y se habilita el volumen elasticsearch_server para alojar los nodos.

#### Magento233

Viene Magento version CE 2.3.3 instalado, la url predeterminada para el acceso al fronted es [xpec.magento.co](xpec.magento.co), para el admin [xpec.magento.co/admin](xpec.magento.co/admin).
el usuario es *xpec_admin* y la contraseña *qpalwosk10*, el nombre de la base de datos es *magento233*.

##### Instrucciones de uso:

-0. Instalar docker y docker-compose.
-1. Copiar / clonar / descargar este archivo o repositorio.
-2. Revisar que las configuraciones predeterminadas sean las que necesitas.
-3. Acceder desde la consola a la carpeta donde se encuentra este proyecto.
-4. Ejecutar el siguiente comando sin comillas *" docker-compose build; docker-compose up -d "*
-5. para acceder a los contenedores basta con ejecutar el comando *" docker exec -it --nombre del contenedor- bash "*.
-6. para apagar el ambiente completo *" docker-compose stop "* para encederlo el ambiente completo *" docker-compose start "*
