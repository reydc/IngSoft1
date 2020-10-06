# Módulo de Partidas

[TOC]

------



## Alcance (Módulo de Partidas)

------



##### Generales del módulo

Este módulo contiene lo relativo a la gestión de partidas y su funcionamiento en general durante el juego. Aquí van a ir los elementos que permitan manipular la partida y sus estados, es decir los bloques que permiten el proceso del juego. Abarca los procesos relacionados a la creación, búsqueda, preparación, comunicación e interacción entre jugadores, control general del estado de la partida, inicialización y finalización de partidas. Este módulo también procesa los resultados de cada partida finalizada y los prepara para registrarlos con el propósito de ser consultados por aquellos usuarios que participaron.



------



##### Objetivos del módulo

* Proveer el subsistema de gestión de partidas:

  Creación.

  Preparación (incluyendo el establecimiento de los jugadores).

  Inicio de partida.

  Fin de partida.

  Control general y organización del estado de la partida.

  Comunicación entre jugadores.

  Procesamiento de resultados.



------



##### Entregables del módulo

1. Alcance del módulo de Partidas.
2. Casos de uso solicitados (otros se han agregado para intentar comprender el comportamiento).

   - Creación de partida
   - Búsqueda y unión a una partida
   - Escribir en el chat de la partida
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



## Casos de uso (Módulo de Partidas)

------



##### Caso de uso #1: Usuario crea una partida (SOLICITADO)

###### Actor primario: Usuario

###### Precondición: El usuario está logueado, confirmado, y ha solicitado su menú de juego

###### Escenario exitoso principal

1. El usuario usa el sistema y pide la creación de una nueva partida.
2. El sistema solicita al usuario que establezca el rango de jugadores aceptados e informa que si no lo hace establecerá un rango por defecto.
3. El usuario establece el rango pedido o no, y usa una opción para terminar de crear la partida.
4. El sistema termina de establecer una partida, la cual queda registrada y es pública.
5. El sistema asigna el jugador creador al usuario y le hace saber el éxito de creación al usuario. 
6. El usuario pasa a ser jugador y queda en espera mientras obtiene en tiempo real un indicador de si se cumplen las condiciones para iniciar la partida.

###### Escenarios alternativos

3. a) El usuario establece un rango que no es válido.

   El sistema informa al usuario qué debe rango puede ingresar y le presenta la misma opción.



------



##### Caso de uso #2: Usuario busca y se une a una partida (SOLICITADO)

###### Actor primario: Usuario

###### Precondición: El usuario está logueado, confirmado, y ha solicitado su menú de juego

###### Escenario exitoso principal

1. El usuario le pide al sistema ver las partidas disponibles para jugar.
2. El sistema le presenta una lista de nombres de partidas no iniciadas, el rango aceptable de jugadores y el número de jugadores actuales.
3. El usuario elige una partida y usa una opción para unirse a la partida.
4. El sistema asigna un jugador al usuario.
5. El usuario pasa a ser jugador y queda en espera, mientras se le informa que el chat de la partida está habilitado en una pestaña.

###### Escenarios alternativos

2. a) No hay partidas.

   El sistema informa al usuario y le pide que intente en otro momento. Se le presenta su menú de juego.

3. a) El usuario no puede unirse porque otro usuario acaba de solicitar unirse a la partida y se llegó al máximo de jugadores para el rango.

   Se informa al usuario y se le devuelve al menú de juegos.

   b) El usuario no puede unirse porque se acaba de iniciar la partida.

   Se informa al usuario y se le devuelve al menú de juegos.



------



##### Caso de uso #3: Jugador abandona la partida

###### Actor primario: Jugador

###### Precondición: El usuario asignado al jugador se ha unido a la partida (no la ha creado) de forma exitosa y la partida no se ha iniciado

###### Escenario exitoso principal

1. El usuario, como jugador, usa una opción para abandonar la partida.
2. El sistema desliga al usuario de su jugador, elimina al jugador y actualiza el estado de la partida.
3. El usuario queda desligado de la partida y se lo devuelve a su menú de juego.

###### Escenarios alternativos

   1. a) La partida inicia en ese momento.

      El jugador no puede abandonar la partida. 



------



##### Caso de uso #4: Jugador creador inicia la partida 

###### Actor primario: Jugador creador

###### Precondición: Se cumple el rango de jugadores necesario para iniciar la partida

###### Escenario exitoso principal

1. El usuario creador, como jugador creador, usa la opción de iniciar la partida.

2. El sistema registra la partida como iniciada y también datos sobre la partida en ese instante. Además:

   1. Inhabilita la opción de abandonar la partida a los jugadores.
   2. Mezcla las proclamaciones del juego.
   3. El Marcador de Elecciones se inicializa.
   4. Designa al primer candidato a Ministro de Magia.
   5. Crea el primer turno de la partida.
3. De acuerdo al número de jugadores actuales:
   1. Designa los roles de los jugadores (y con ello, la lealtad y el equipo). 
   2. Prepara un tablero con los hechizos que pueden ser desbloqueados.

4. Se informa a cada jugador sus datos para el juego y además cada mortífago tiene una lista de quiénes son sus compañeros.

5. Se despliega gráficamente los elementos del juego, donde se muestran los datos que corresponden al turno y deban ser públicos, los cargos de Ministro de Magia y Director, quiénes están designados en los cargos y si son candidatos o elegidos. Además se despliegan los elementos gráficos particulares para cada jugador.

###### Escenarios alternativos

1. a) Un jugador acaba de abandonar la partida y no se llega al mínimo número de jugadores del rango de la partida.

   Se actualiza el indicador de inicio de la partida notificando que no se puede iniciar.



------



##### Caso de uso #5: Jugador escribe en el chat de la partida (SOLICITADO)

###### Actor primario: Jugador

###### Precondición: El jugador se ha unido exitosamente a una partida

###### Escenario exitoso principal

1. El usuario, como jugador, abre la pestaña del chat, escribe su mensaje y usa la opción de envío.
2. El sistema actualiza el chat para todos los jugadores, indicando quién envía el mensaje.

###### Escenarios alternativos

1. a) El jugador no está habilitado para usar el chat, es decir, está en un cargo durante una sesión legislativa o ha sido asesinado.

   El jugador puede ver el chat, pero no escribir, teniendo la opción de enviar funcionalmente deshabilitada.



------



##### Caso de uso #6: Finalización de la partida

###### Actor primario: Sistema

###### Precondición: Se han cumplido alguna de las condiciones de victoria del juego

###### Escenario exitoso principal

1. El sistema revisa el estado de la partida y fija a un equipo como victorioso.
2. El sistema recopila los resultados generales de la partida y de cada usuario como jugador de la partida, luego registra los resultados.
3. El sistema informa a cada jugador el resultado del juego.
4. El sistema desliga a cada usuario participante de su jugador y lo redirije a su menú de juego.
5. El sistema elimina/destruye la partida.

###### Escenarios alternativos

​    Ninguno.



------



## Diccionario de Datos (Módulo de Partidas)

------

* Datos primitivos: 
  
  * minimo_jugadores, maximo_jugadores
  
  * email_usuario, nombre_usuario
  
  * id_jugador
  * true, false
  * nombre_partida, numero_jugadores
  * rol, lealtad
  * numero_turno, etapa_turno
  * lumos, nox
  * hechizo, accion_legislativa
  * informacion_victoria
  * equipo_ganador
  * equipo
  * veces_ministro_de_magia, veces_director
* Otros datos:
  * datos_nueva_partida = email_usuario + nombre_usuario + minimo_jugadores + maximo_jugadores
  * creador = true | false
  * datos_jugador = id_jugador + creador
  * datos_jugadores = [ datos_jugador ]*
  * partida_iniciada = true | false
  * partida = nombre_partida + partida_iniciada + minimo_jugadores + maximo_jugadores + numero_jugadores
  * partida_sin_iniciar = nombre_partida + partida_iniciada + minimo_jugadores + maximo_jugadores + numero_jugadores
  * datos_usuario = email_usuario + nombre_usuario
  * nuevos_datos_partida = nombre_partida + numero_jugadores
  * turno = numero_turno + etapa_turno
  * voto = lumos | nox
  * datos_acciones_jugador = voto | accion_legislativa | hechizo
  * resultado_partida = nombre_partida + equipo_ganador + numero_jugadores + fecha_creacion + hora_inicio + hora_fin
  * ganador = true | false
  * fue_voldemort = true | false
  * resultado_usuario = nombre_partida + ganador + equipo + fue_voldemort + veces_ministro_de_magia + veces_director 
  * resultados_usuarios = [ resultado_usuario ]*



------



## Diagramas (Módulo de Partidas)

Próximas páginas.



------

