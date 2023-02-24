# PicaPoint, S.L.

## __Manual de instalación__
* ### _base de datos_
Se necesita antes de nada clonar el repositorio __db__ en local, y posteriormente ejecutar el script __global.sql__ en el gestor de base de datos _MySQL_ para crear la base de datos y las tablas necesarias para el correcto funcionamiento del programa.

Para ejecutar el script se ha de tener la carpeta de mysql en el path de las variables de entorno, para asi acceder al comando _mysql_ desde cualquier parte del terminal, y posteriormente ejecutar el comando __mysql -u root -p__ desde la carpeta descargada del repositorio _db_, y posteriormente ejecutar el comando __source global.sql__ para ejecutar el script y crear las tablas necesarias con los datos insertados por defecto.

* ### _Servidor_
Clonar el repositorio remoto de __server__ en local y posteriormente es recomendable iniciarlo en algún entorno de desarrollo como IntelliJ, ya que exportanto el servidor en formato _.jar_, puede dar lugar a errores inesperados.

El servidor contiene las plantillas HTML de la web necesarias para funcionar, por tanto, una vez arrancado el servidor con el IntelliJ, ya solo faltaría dirigirse a [localhost](localhost:8080) en el puerto _8080_ para visualizar la web.

## __Manual de uso__
* ### _web_ 
Tanto los administradores como los clientes establecerán la comunicación con el servidor y la base de datos a traves de la web, donde la única ruta no protegida será /login, la cual nos permite acceder y obtener las credenciales necesarias para visualizar la web completa y acceder al area personal de cada usuario.

Un usuario por defecto que se crea cuando se insertan datos en mysql, es _admin_ _admin_, asi que podemos usarlo para probar la web.

* ### _ESP8266_
cada una de estas placas irán instaladas en una máquina dispensadora, donde se activará el pin correspondiente al producto que vaya a caer, y acto seguido mandará al servidor esta información que, estará compuesta por la MAC de la propia placa junto a la id del producto del pin activado. Al recibir esto, el servidor interpretará que se ha producido una venta y por tanto restará 1 en la base de datos a la cantidad restante de dicho producto en dicha máquina especifica.

Debido a que no disponemos de una maquina dispensadora para probar los pins, se generará un archivo html y se mostrará desde un servidor creado por la propia placa. Desde allí se visualizará un input, que se completará manualmente con la id del producto a restar y un botón que hará la petición al servidor.

Hay que tener en cuenta que si el servidor recibe el id de un producto que no pertenece a la máquina, devolverá un _StatusCode: 404_