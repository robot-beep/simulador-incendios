# simulador-incendios
proyecto de simulador de incendios en netlogo, para la primera tarea de la asignatura "simulación basada en agentes". 

descripción del modelo: 

2.1. propósito
Simular la propagación de un incendio en un bosque con tres tipos de árboles, teniendo en cuenta la capacidad de combustible de cada árbol, la velocidad de combustión y el calor generado por kg de combustible quemado.

2.2. entidades, variables de estado y escalas

2.2.1. Entidades:
Los agentes en esta simulación son las "patches" o parcelas, cada una de las cuales puede tener uno de los tres tipos de árboles o estar vacía.

2.2.2. Variables de estado de las parcelas y escalas:

1.	tipo: Tipo de árbol (1, 2, 3 o 0 si no hay árbol). No posee escala.
2.	C: Capacidad potencial de combustible en Kg. 
3.	V: Velocidad de combustión en Kg/min.
4.	Qj: Calor generado por kg de combustible quemado °C/Kg.
5.	combustible: Cantidad de combustible restante en Kg. 
6.	calor: Calor total generado por este patch en °C.
7.	encendido: Booleano que indica si el árbol está encendido o no.
8.	Q: variable global que representa la densidad del bosque. 

2.3. Resumen del proceso y programación
En cada paso (tick) del modelo:
1.	Se calcula cuánto calor se genera.
2.	Se determina qué árboles se encienden debido al calor de sus vecinos.

2.4. Conceptos de diseño
2.4.1. Principios Básicos
Un árbol se incendia si la suma del calor de los árboles que están en la misma parcela y en las parcelas vecinas (vecindad de Moore) supera un umbral de calor Q.

2.4.2. Interacción
La interacción ocurre entre un árbol y sus vecinos directos. Un árbol puede incendiarse debido al calor generado por los árboles vecinos.

2.4.3. Observación
El estado de cada parcela se observa en función de su color, que representa si está quemado, está ardiendo o está intacto.

2.5. Detalles
2.5.1. Inicialización
Se establece el valor global Q.
Cada parcela decide si tendrá un árbol basándose en la densidad-arboles. Si tiene un árbol, se asigna un tipo al azar (1, 2 o 3) y se inicializan sus variables asociadas.
Se enciende al azar un árbol que no esté en una parcela vacía.
3.2 Input data
El modelo utiliza los valores para densidad-arboles, C, V, Qj y Q como entradas.

2.5.2. Submodelos
configurar-arbol: Establece los valores de C, V y Qj para un árbol basándose en su tipo.
simular: Calcula la propagación del fuego en cada paso.
ajustar-color: Ajusta el color del árbol en función de la cantidad de combustible que ha sido quemado.
