# Módulo de Usuarios

[TOC]

------



## Alcance (Módulo de Usuarios)

------



##### Generales del módulo

Este módulo contiene lo relativo a la gestión básica de los usuarios (confirmados o no) que harán uso del sistema pedido. Abarca los procesos de registrar, autenticar y actualizar datos de los usuarios en el sistema propuesto. También es el encargado de procesar datos relacionados al historial de las partidas en las que participó el usuario.

El módulo no abarca al usuario en la dinámica del juego (o sea que no se lo toma como jugador), pero es necesario durante la creación y el proceso del juego.



------



##### Objetivos del módulo

* Proveer el subsistema básico de gestión de usuarios:

  Registro.

  Ingreso.

  Validación y verificación de datos de usuario.

  Confirmación del usuario.

  Autenticación básica.

* A su vez el mecanismo de autogestión para los mismos:

  Actualización de los datos por cada usuario, con excepción del dato inmutable que se usa para identificar al usuario, al menos a nivel del análisis.
  
  Historial de partidas con números relacionados a la participación en partidas.



------



##### Entregables del módulo

1. Alcance del módulo de Usuarios.
2. Casos de uso solicitados (otros se han agregado para intentar comprender el comportamiento).

   - Registrarse
   - Actualizar datos del perfil
   - Modificar password
3. Diagrama de flujos de datos.
4. Diagrama de clases.



------



##### Criterios de aceptación

* Será evaluado por los profesores del práctico y teórico.
* Añadirán los comentarios y correcciones relevantes.



------



##### Limitantes presupuestarios

* Se usarán los recursos que estén disponibles durante el cursado de la materia.

 

------



## Casos de uso (Módulo de Usuarios)

------



##### Caso de uso #1: Cliente se registra (SOLICITADO)

###### Actor primario: Cliente

###### Precondición: Ninguna

###### Escenario exitoso principal

1. El cliente usa el sistema para ingresar datos solicitados (email, nombre, password, avatar/foto).

2. 1. Por cada dato solicitado, el sistema hace las validaciones correspondientes.

   2. El sistema crea un usuario registrando los datos solicitados.

3. Se hace saber el éxito al cliente y se redirecciona a la página principal de logueo y registro.

###### Escenarios alternativos

2. a) Algún dato ingresado no es válido.

   El sistema informa al cliente qué debe ingresar para que sea válido el dato solicitado, y debe reintentar el proceso.

   b) El sistema no puede crear un usuario o no puede registrar todos los datos solicitados.

   El sistema informa la situación al cliente, descarta todos los datos ingresados y las entidades lógicas temporales.



------



##### Caso de uso #2: Cliente se loguea

###### Actor primario: Cliente

###### Precondición: Ninguna

###### Escenario exitoso principal

1. El cliente usa el sistema para ingresar su email y password.

2. El sistema verifica que los datos ingresados se corresponden con algún usuario.

3. El sistema otorga al cliente sus datos de usuario y queda logueado (se cambia el estado del usuario a activo), además informa al cliente del éxito. Después se redirecciona al menú principal que muestra al usuario:

   Una opción para <u>acceder a sus datos de perfil</u> (Caso de uso #3)

   Una opción para <u>acceder a su menú de juego</u> (Caso de uso #7)

   Una opción para <u>desloguearse</u> (o cerrar sesión) (Caso de uso #8)

###### Escenarios alternativos

2. a) Alguno de los datos ingresados no son válidos individualmente o en conjunto.

   El sistema informa la situación al cliente y solicita que vuelva a ingresar los datos solicitados para loguearse o que registre un usuario.



------



##### Caso de uso #3: Usuario accede a su perfil 

###### Actor primario: Usuario

###### Precondición: El usuario está logueado, no está jugando una partida y no está en su menú de juego

###### Escenario exitoso principal

1. El usuario solicita al sistema su perfil.
2. El sistema muestra al usuario sus datos y le da opciones que se corresponden al usuario (casos de uso #4, #5, #6).

###### Escenarios alternativos

​    Ninguno.



------



##### Caso de uso #4: Usuario actualiza sus datos de perfil (SOLICITADO)

###### Actor primario: Usuario

###### Precondición: El usuario accedió a su perfil y no está jugando ninguna partida

###### Escenario exitoso principal

1. El usuario solicita al sistema actualizar su perfil.

2. El sistema informa las opciones al usuario (los subcasos de uso #4.1, #4.2, #4.3).

3. El usuario ejecuta las acciones correspondientes a los subcasos según su elección:

   <u>Modificar su nombre</u> (Caso de uso #4.1)

   <u>Modificar su avatar</u> (Caso de uso #4.2)

   <u>Modificar su password</u> (Caso de uso #4.3)

###### Escenarios alternativos

3. a) Ocurrió algo anormal durante la modificación de los datos.

   El sistema informa al usuario de acuerdo a la primera excepción en el subcaso de uso.



------



##### Caso de uso #4.1: Usuario actualiza su nombre

###### Actor primario: Usuario

###### Precondición: El usuario solicitó actualizar su perfil

###### Escenario exitoso principal

1. El usuario ingresa el nuevo nombre que desea para su perfil.

2. 1. El sistema valida el nombre.

   2. Actualiza el usuario y los registros.

3. Se hace saber el éxito al usuario.

###### Escenarios alternativos

2. a) El nombre ingresado no es válido.

   El sistema informa al usuario, y el nombre no se modifica. Además se descartan las entidades lógicas temporales que se pudieran haber usado.



------



##### Caso de uso #4.2: Usuario actualiza su avatar

###### Actor primario: Usuario

###### Precondición: El usuario solicitó actualizar su perfil

###### Escenario exitoso principal

1. El usuario actualiza/sube/ingresa el nuevo avatar que desea para su perfil.
2. 1. El sistema valida el avatar.
   2. El sistema actualiza al usuario y los registros.
3. Se hace saber el éxito al usuario.

###### Escenarios alternativos

2. a) El avatar elegido para actualizar no es válido.

   El sistema informa al usuario, y el avatar no se modifica. Además se descartan las entidades lógicas temporales que se pudieran haber usado.



------



##### Caso de uso #4.3: Usuario actualiza su password (SOLICITADO)

###### Actor primario: Usuario

###### Precondición: El usuario solicitó actualizar su perfil

###### Escenario exitoso principal

1. El usuario ingresa su password actual.
2. El sistema procesa y verifica que el password se corresponde con el del registro del usuario, luego informa al usuario y pide el nuevo password.
3. El usuario ingresa el nuevo password que desea para su perfil.
4. 1. El sistema valida el nuevo password.
   2. El sistema actualiza al usuario y los registros.
5. Se hace saber el éxito al usuario.

###### Escenarios alternativos

2. a) El password no se corresponde con el usuario.

   El sistema informa al usuario y solicita que lo vuelva a intentar.

3. a) El nuevo password no es válido.

   El sistema informa al usuario, y el password no se modifica. Además se descartan las entidades lógicas temporales que se pudieran haber usado.



------



##### Caso de uso #5: Usuario confirma su email

###### Actor primario: Usuario

###### Precondición: El usuario accedió a su perfil y no está confirmado 

###### Escenario exitoso principal

1. El usuario pide al sistema confirmar su email.
2. El sistema prepara un [trigger](#a1) para la confirmación e informa al usuario de que forma puede activarlo y quién es el proveedor de confirmación.
3. El usuario activa el trigger por medio del proveedor de confirmación, y se envía una respuesta al sistema.
4. 1. El sistema valida la respuesta de confirmación
   2. El sistema actualiza al usuario y los registros.
5. Se hace saber el éxito al usuario.

###### Escenarios alternativos

4. a) La respuesta de confirmación no es válida.

   El sistema informa al usuario que no ha cumplido las condiciones para quedar confirmado, se descartan las entidades lógicas temporales que se pudieran haber usado y no se modifica el estado de no-confirmado del usuario.



------



##### Caso de uso #6: Usuario solicita su historial de partidas

###### Actor primario: Usuario

###### Precondición: El usuario accedió a su perfil y está confirmado 

###### Escenario exitoso principal

1. El usuario solicita ver su historial de partidas.
2. El sistema despliega su historial de partidas.

###### Escenarios alternativos

​    Ninguno.



------



##### Caso de uso #7: Usuario solicita su menú de juego

###### Actor primario: Usuario

###### Precondición: El usuario está logueado, confirmado, no está jugando una partida y no está revisando su perfil

###### Escenario exitoso principal

1. El usuario solicita ver su menú de juego.
2. El sistema despliega su menú de juego con las opciones correspondientes (ver el Módulo de Partidas).

###### Escenarios alternativos

​    Ninguno.



------



##### Caso de uso #8: Usuario se desloguea

###### Actor primario: Usuario

###### Precondición: El usuario está logueado y no está jugando ninguna partida

###### Escenario exitoso principal

1. El usuario pide desloguearse (o cerrar sesión) al sistema.
2. El sistema cambia el estado del usuario y registra que no está activo.
3. El Usuario pasa a ser un cliente más y se redirecciona a la página principal de logueo y registro.

###### Escenarios alternativos

​    Ninguno.



------



##### Notas

* <a name="a1">trigger</a>: 

  Hacemos uso de esta palabra (traducible como "disparar" o "desencadenar") para referirnos a un proceso que el sistema prepara para capturar un evento y para el cual un actor debe activar o cumplir ciertas condiciones para que ese evento ocurra y el sistema lo capture.



------



## Diccionario de Datos (Módulo de Usuarios)

------

* Datos primitivos: 
  * nombre, nuevo_nombre
  * avatar, nuevo_avatar
  * email, nuevo_email, email_login
  * password, nuevo_password, password_login
  * true, false
  * historial_general_usuario
  * historial_partida_usuario
  * mensaje
  * trigger_confirmacion

* Otros datos:
  * datos_registro = email + nombre + avatar + password
  * ok_email = true | false
  * ok_nombre = true | false
  * ok_avatar = true | false
  * ok_password = true | false
  * success_registrar = true | false
  * data_login = email_login + password_login
  * email_login_verificado = true | false
  * password_login_verificado = true | false
  * success_login = true | false
  * emails = [ email ]*
  * passwords = [ password ]*
  * datos_usuario = email + nombre + avatar
  * password_verificado = true | false
  * historial_partidas = [ historial_partida_usuario ]*
  * historial_usuario = historial_general_usuario + [ historial_partida_usuario ]*
  * respuesta_confirmacion = mensaje + [ true | false ]
  * email_confirmado = true | false
  * usuario_activo = email_login +  true
  * usuario_no_activo = email + false



------



## Diagramas (Módulo de Usuarios)

Próximas páginas.



------

