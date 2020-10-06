# Módulo de Turno

[TOC]

------



## Alcance (Módulo de Turno)

------



##### Generales del módulo

Este módulo contiene los pasos y acciones que se dan durante la dinámica del juego mismo. Se encarga del proceso de elecciones, la sesión legislativa y las acciones ejecutivas subsiguientes, interactuando con otras partes del sistema para proveer funciones, estados de la partida, otorgando poderes y avanzando en el juego.



------



##### Objetivos del módulo

* Proveer las etapas de un turno del juego:

  Etapa de elecciones.

  Etapa de sesión legislativa.

  Etapa de acciones ejecutivas.

* Contribuir a la dinámica del juego:

  El estado de la partida se va modificando en cada turno.

  Los jugadores tienen permitidas ciertas cosas mientras se le restringen otras, en cada turno.

  El Ministro de Magia y el Director pueden acceder a hechizos.

* Chequear las condiciones de victoria para alguno de los equipos:

  * Victoria de los Mortífagos:
    * Logran seis (6) promulgaciones de sus proclamaciones.
    * Logran que Voldemort sea Director después de promulgar tres (3) o más de sus proclamaciones.

  * Victoria de la Orden del Fénix:
    * Logran cinco (5) promulgaciones de sus proclamaciones.
    * Voldemort es asesinado (no importa por quién).



------



##### Entregables del módulo

1. Alcance del módulo de turno.
2. Casos de uso solicitados (otros se han agregado para intentar comprender el comportamiento).

   - Elección del Ministro de Magia y el Director
   - Sesión legislativa
   - El Ministro de Magia usa el "Avada Kedavra"
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



## Casos de uso (Módulo de Turno)

------



##### Caso de uso #1: Selección del candidato a Director

###### Actor primario: Sistema

###### Precondición: Durante el turno anterior no hubo victoria para ningún equipo y el sistema eligió a un candidato a Ministro de Magia o alguien eligió al candidato a Ministro de Magia por el hechizo "Imperius"

###### Escenario exitoso principal

1. El sistema le presenta al candidato a Ministro de Magia una lista de candidatos a Director elegibles.
2. El candidato a Ministro de Magia selecciona a un candidato y usa una opción para elegir al candidato a Director.
3. El sistema notifica a cada jugador la fórmula candidata al gobierno. 

###### Escenarios alternativos

​    Ninguno.



------



##### Caso de uso #2: Elección del gobierno (SOLICITADO)

###### Actor primario: Sistema

###### Precondición: El candidato a Ministro de Magia ha elegido a un candidato a Director

###### Escenario exitoso principal

1. El sistema indica a cada jugador los candidatos.

2. Cada jugador que no ha sido eliminado en la partida puede votar:

   Si vota "lumos", se cuenta como un voto a favor de la fórmula.

   Si vota "nox", se cuenta como un voto en rechazo a la fórmula.

3. El sistema recibe los votos, pero no revela nada hasta que todos han votado. Cuando todos han votado, informa el resultado a los jugadores y muestra a cada jugador como fue el voto de los otros.

4. El sistema designa a las nuevas autoridades de Hogwarts si la mayoría de votos fueron "lumos" y se pasa a la siguiente etapa del turno (Caso de uso #3). Si hay empate o la mayoría de los votos fueron "nox" los jugadores rechazan la fórmula, el Marcador de Elección se incrementa y se acaba el turno.

###### Escenarios alternativos

4. a) Ocurre la condición de victoria por elección de Voldemort.

   Se revela a los jugadores quién es Voldemort y se declara ganador al equipo de los Mortífagos. El sistema finaliza la partida.



------



##### Caso de uso #3:  Sesión legislativa (SOLICITADO)

###### Actor primario: Sistema

###### Precondición: Las autoridades acaban de ser elegidas y no se cumple la condición de victoria de los Mortífagos por elección de Voldemort y el número de promulgaciones

###### Escenario exitoso principal

1. El sistema le muestra tres proclamaciones privadamente (no se revela a ningún otro jugador ) al Ministro de Magia. También se le deshabilita el chat al Ministro de Magia y al Director.
2. El Ministro de Magia usa una opción para descartar una proclamación.
3. El sistema deja de mostrar las proclamaciones al Ministro de Magia y revela privadamente las proclamaciones no descartadas al Director.
4. El Director usa una opción para descartar una proclamación y usa una opción para promulgar la otra.
5. El sistema revela la proclamación promulgada a los jugadores y la posiciona en el tablero del juego (públicamente), y si la posición desbloquea un hechizo se notifica a todos los jugadores.  Se habilita el chat del Ministro de Magia y el Director.

###### Escenarios alternativos

1. a) Hay menos de tres proclamaciones disponibles para el Ministro de Magia.

   El sistema chequea esto y mezcla las proclamaciones no promulgadas (las disponibles y las descartadas) y se las deja disponibles a todas. Luego se procede a repetir este caso de uso.

4. a) El Director invoca el hechizo "Expelliarmus".

   Si el Ministro de Magia decide acompañar al hechizo "Expelliarmus" se descartan las dos proclamaciones del Director y se incrementa el Marcador de Elección. De otra forma el Director debe promulgar una proclamación y descartar la otra proclamación, y por último se sigue como en el paso 5 del escenario exitoso principal de este caso de uso.

5. a) Ocurre la condición de victoria por elección de Voldemort, cuando el Director es Voldemort y hay tres proclamaciones de Mortífagos.

   Se revela a los jugadores que el Director es Voldemort y se declara ganador al equipo de los Mortífagos. El sistema finaliza la partida.

   b) Ocurre la condición de victoria de los Mortífagos por la promulgación de seis de sus proclamaciones.

   Se declara ganador al equipo de los Mortífagos. El sistema finaliza la partida.

   c) Ocurre la condición de victoria de la Orden del Fénix por la promulgación de cinco de sus proclamaciones.

   Se declara ganador al equipo de la Orden del Fénix. El sistema finaliza la partida.



------



##### Caso de uso #4: El Ministro de Magia usa el "Avada Kedavra" (SOLICITADO)

###### Actor primario: Ministro de Magia

###### Precondición: Sesión legislativa ha terminado y se ha desbloqueado el hechizo "Avada Kedavra"

###### Escenario exitoso principal

1. El Ministro de Magia elige de una lista de jugadores a quién eliminar y usa una opción habilitada que dice "Avada Kedavra".
2. El sistema informa al resto de los jugadores que el jugador seleccionado ha sido eliminado. El sistema deshabilita el chat y la opción de votar para el jugador eliminado, y también pasa a ser no elegible para un cargo. El sistema acaba el turno.

###### Escenarios alternativos

2. a) Ocurre la condición de victoria de la Orden del Fénix eliminando a Voldemort.

   Se informa al resto jugadores que el jugador es Voldemort y se declara ganador al equipo de la Orden del Fénix. El sistema finaliza la partida.



------



## Diccionario de Datos (Módulo de Turno)

------

* Datos primitivos: 
  
* id_jugador
  * nombre_usuario
  * true, false, si, no
  * lumos, nox
  * marcador_eleccion
  * proclamacion
  * hechizo
  * tablero_de_partida
  
* Otros datos:
  
  * candidatos_director_elegibles = [ id_jugador + nombre_usuario ]*
  
  * candidato_ministro_de_magia = id_jugador + nombre_usuario
  * candidato_director = id_jugador + nombre_usuario
  * voto = lumos | nox
  * resultado_votacion = si | no
  * caos = true | false
  * finalizar_partida = true | false
  * proclamaciones_promulgadas_mortifagos = [ proclamacion ]*
  * proclamaciones_promulgadas = [ proclamacion ]*
  * proclamaciones_disponibles = [ proclamacion ]*
  * tripla_proclamaciones = proclamacion + proclamacion + proclamacion
  * par_proclamaciones = proclamacion + proclamacion
  * proclamacion_promulgada = proclamacion
  * proclamacion_descartada = proclamacion
  * par_proclamaciones_descartadas = proclamacion + proclamacion
  * proclamaciones_descartadas = [ proclamacion ]*
  * hechizo_ejecutado = true | false



------



## Diagramas (Módulo de Turno)

Próximas páginas.



------

