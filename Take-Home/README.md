# Take-Home (2020)

Consiste en hacer analisis de tres módulos de una posible implementación del juego "Secret Voldemort":

* Módulo de Usuarios
* Módulo de Turno
* Módulo de Partidas

Para cada uno de ellos se debe entregar:

- Alcance del módulo
- Tres casos de uso
- Diagrama de flujo de datos
- Diagrama de clases

Tiempo de entrega: 1 semana y 5 días

---

## Observaciones sobre proyectos de este tipo (alumno)

Algunas lecciones que he obtenido haciendo el proyecto.  

#### Comprensión del problema  

- El enunciado es claro. Hay un juego de mesa que tiene un reglamento que prescribe como se desarrolla, sus reglas y situaciones excepcionales, los elementos para el desarrollo del juego, las etapas de desarrollo del juego, los participantes, etc. Si no nos dieran el reglamento y nos dieran una tarea para el cual habría que observar el comportamiento de un sistema (por ejemplo otro juego) deberíamos considerar ítems igualmente parecidos. Entonces el proyecto queda simplificado por ese lado.  

- Sin embargo nos piden desarrollar módulos en un mismo producto. En este caso parece que la dificultad es la descripción consistente, en distintos niveles, de los módulos y la posible interacción entre ellos. Entonces hay que considerar como organizar cada módulo de forma que esa organización tenga una alta cohesión y un bajo acoplamiento para las tareas que son requeridas en el proyecto, cuidando la comunicación con los clientes (profesores).  

- Las decisiones en la etapa de análisis son impactadas por cierta concepción en el posible diseño. Acá podemos apreciar cómo es que el modelado y el análisis nos pueden llevar a diseñar muchos más aspectos de los que realmente deseamos o que tengamos un cierto sesgo hacia diseñar cuando nos piden modelar.  

#### Casos de uso  

- Se derivan de observar el reglamento, y los huecos que pudieran haber en la descripción de los casos de uso (a partir de la descripción del comportamiento entre los jugadores) se los completa con los requerimientos y aspectos pedidos por los clientes. La ventaja es que como existe un reglamento debemos respetar prioritariamente las reglas y después observar lo que piden específicamente los clientes.  

- En este proyecto se piden tres casos de uso, pero puede ocurrir que para que hay un desarrollo consistente, de acuerdo a las reglas, sea necesario desarrollar aquellos que sean "adyacentes" a ellos. En este caso tenemos una ayuda más para comprender el problema visto desde este punto de vista.  

- Por el punto anterior es factible que cuando hayamos completado un caso de uso más "adyacente" respecto a otro tengamos más información para corregir al otro, pudiendo desafiar nuestras presunciones acerca de las precondiciones, los actores, los escenarios alternativos o la posible adición/eliminación de subcasos. Incluso podemos obtener información de un caso de uso para un módulo cuando terminamos un caso de uso de un módulo que es de más "bajo nivel" o que sería un submódulo de este último. También debemos considerar que si los módulos sirven para gestionar servicios más generales, las partes dinámicas de cierta pieza de software, las partes estáticas, y las interacciones entre subsistemas.  

- Si no vemos un módulo que estaría ejerciendo un cierto control o chequeo, no significa que este no exista. De alguna forma se chequean algunas condiciones de control para pasar de un comportamiento o conjunto de comportamientos a otros. Imaginar que están ahí, aún cuando nos centremos en lo que ocurre en el módulo objetivo.  

#### Diagrama de Flujo de Datos  

- Hay que hacer un esfuerzo consciente para no pasar flags o "variables de control" que no sean realmente datos para los procesos. En tal caso estaríamos pensando en condiciones y los procesos sujetos a ejecución según esas condiciones.  

- Considerar que transformaciones de datos se corresponden con los casos de uso ¿Están todos? ¿Qué falta? ¿Por qué falta? ¿Realmente se lo puede agregar al DFD o más bien implicaría un procedimiento y no una transformación? ¿Qué transformación de datos implica si no es una transformación en sí?

- Es más fácil agregar cosas que extraerlas. 

- Las flechas que contienen, exclusivamente, información de control deberían ser eliminadas. Si llevan información sobre cierta condición deberían acompañar otros datos que no sean de control sino que sirvan para hacer una transformación necesaria o eliminar esa información que indique la condición, pues lo que interesa es lo que se transforma.  

- Cuando se éste construyendo el Diccionario de Datos, considerar que datos serían los más primitivos y cuales serían los más compuestos. Un dato que es básico o suponemos dado en un módulo no necesariamente es un dato básico en otro. Si hay más de un módulo y uno da cuenta de cómo está compuesto cierto dato, en otro módulo podemos considerarlo como referencia. 

#### Diagrama de clases  

- 

- 

---

## Feedback (evaluación)

* Se hace énfasis en la comunicación verbal y ser preciso. Quizá está bien tratar de explicar el proceso por el cual se decidió tomar una clase como parte de otra, una burbuja como un proceso de alto nivel, o la interpretación de un enunciado sobre los requerimientos por parte de un profesor.  

* Se hace énfasis en considerar el proyecto como una forma de construir los puntos de vista del sistema.  

* Cuando dicen ser general respecto al alcance se refieren a explicar desde lo general del software (en este proyecto nos referimos concretamente al juego "Secret Voldemort") hasta el módulo, no partiendo del módulo que se toma para evaluar.  

* En general los casos de uso se basan en lo intercambiado con los profesores y esto se intentó hacer ver reflejado en la descripción de cada uno de ellos. Un tema importante es la consistencia entre diagramas y los casos de uso. En la forma en que hice este proyecto no se ve del todo y esto se debe a que se estuvo trabajando y modificando los diagramas mientras se redactaban y modificaban los casos de uso. En consecuencia ocurrieron inconcistencias a nivel de relación de elementos y agregación/eliminación de elementos, tanto para las clases propuetas como para los procesos pensados y reflejados en el DFD.  

* Otros problemas pueden traer las clases que sirven como medio de interación entre otras clases, ya que tenemos que tener en cuenta qué es lo que intercambian, qué datos deben compartir (se puede traducir en un atributo que es accesible para otras clases), y si es una clase padre para las clases que tienen ciertas relaciones.  

#### Parte de la evaluación (revisión del módulo de Partidas)

Alcance:  
Ser más eficiente en la explicación con el cliente, situar el módulo en el contexto del sistema propuesto (el juego).  

Explicación de casos de uso:  
Aparentemente está lo que se pide.  

Revisión del DFD de Partidas:  
Inconsistencia con los casos de uso, puesto que no figura algo que dé cuenta del chat antes de iniciar una partida. Clara omisión debido a la consideración de sólo los elementos estáticos cuando se instancia algo de clase Partida, y no pensando en la interacción de los jugadores.  

Revisión del DC de Partidas:  
Agregar una clase que no hace nada excepto contener a otra (el Chat estaría compuesto por MensajeChat). Esto ocurrió porque a la hora de entregar no me decidí por mejorar la parte del chat, pues la clase quedaba vacía en atributos o métodos, cuando debería haber tenido atributos que serían compartidos por los clientes del chat (los jugadores) que están correctamente relacionados. Así en los mensajes fueron agregados cosas que no deberían estar controladas por los clientes, como la hora de envío (pues debería considerar que en la forma en que está en el diagrama, parece que la hora de envío es local, mientras que lo que quiero es que sea la hora del servidor). Aspectos del servicio que también se deberían considerar a la hora del análisis del módulo.  
