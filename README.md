# Administrador de Dispositivos de Ubicación

El Administrador de Dispositivos de Ubicación es un microservicio desarrollado con Express y Bookshelf. Permite a las aplicaciones conectadas pasar los números de teléfono de los dispositivos de ubicación (actualmente, solo es compatible con el rastreador GPS GSM Android A8) y hacerles ping. Los resultados se almacenan como un evento móvil en la base de datos y se pueden recuperar mediante llamadas a la API. Actualmente, utilizamos SMS como canal de control del dispositivo y Nexmo como puerta de enlace SMS.

## ¿Por qué usar el Administrador de Dispositivos de Ubicación?

Ofrece una forma cómoda de gestionar dispositivos de ubicación y su historial de eventos.

## ¿Cómo funciona?
El Administrador de Dispositivos de Ubicación utiliza Bookshelf para gestionar bases de datos RDBMS (en el ejemplo, uso MySQL, pero es fácil cambiar a PostgreSQL o SQLite) para almacenar los identificadores de los dispositivos. Próximamente se añadirán tareas (la posibilidad de configurar una programación y una fecha de caducidad para hacer ping a los dispositivos).

## Instalación
Asegúrese de tener MySQL configurado y disponible. Luego:
```$xslt
$ git clone https://github.com/boriskogan81/location-device-manager.git
//...cambiar al directorio /location-device-manager
$ npm install

//Copiar los archivos de la carpeta config_templates a la carpeta config en la raíz.
//Realizar los ajustes necesarios.
//Ejecutar la migración inicial de Knex:

$ knex migrate:latest

$ npm start
```

## Uso
Utilice Location Device Manager como servicio para administrar dispositivos de ubicación o cualquier otro dispositivo basado en SMS.

## Pruebas
Location Device Manager utiliza SQLite en memoria para las pruebas. La interfaz de las bases de datos es la misma (Bookshelf/Knex) que la de la aplicación normal. Las migraciones se ejecutan en cada prueba para garantizar que la estructura de la base de datos esté actualizada. Al finalizar las pruebas, los datos o tablas almacenados desaparecen. ```
$ npm run test
```