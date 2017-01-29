# gacvrp
Algortimo genetico para el problema del ruteo de vehiculo con carga (VRP)

Programa realizado para la Optativa Optimizacion y Combinatorio de la Facultad de Ciencias Exactas UNSA 2016
Utilizando como lenguaje de programacion Python y utilizando como guia PAPERS y demas material bibliografico para implementar dichos algoritmos

## Algoritmo Genetico
En una aproximacion a la realidad, son aplicados en poblaciones o grupos conformados por individuos o cromosomas, cada uno con la capacidad de intercambio de genes por medio de cruzes y evolucion, mientras pasan por un proceso de seleccion; los que mejores genes tengan son los que mas chances tengan de sobrevivir. El pseudocodigo del algoritmo es el siguiente.
while procesoCondicion() do
  for individuo in Poblacion do
    vecinos = ObtenerVecindario(individuo);
    padres = Seleccion(vecinos);
    individuo_aux = Cruze(padres);
    individuo_aux = Mutacion(individuo_aux);
    Reemplazo(Posicion(individuo),individuo_aux);
  end for
end while
### Representacion de los Cromosomas
Para aclarar la representacion del ruteo como cromosoma. Para cada cromosoma pueden utilizar k vehiculos para lograr alcanzar una solucion al problema. Por lo cual cada vehiculo tiene su recorrido, y el conjunto de estos recorridos formarian un cromosoma.
### Generacion de la Poblacion inicial
Los individuos de la poblacion son generados de forma aleatoria y a continuacion son son modificados para forzar que representen soluciones validas al problema.
### Operador de Cruze
El operador de cruce utilizado es generic crossover. Este operador tiene la principal caracteristica de promover de una forma omportante la diversidad en la poblacion.
### Mutacion
La mutacion esta compuesta por cuatro tipos de mutaciones distintas que se aplican con diferentes probabilidades (solo) se aplica una de ellas en cada caso). El uso de estos cuatro operadores de mutacion nos permite modificar el itinerario de una ruta mover clientes entre rutas, y añadir o eliminar rutas, al igual que sucede con el operador de cruce utilizado. Estos operadores son:
#### Intercambio
Consiste en intercambiar la posicion de dos clientes(pertenecientes a la misma ruta o no) elegidos aleatoriamente.
#### Inversion
Invierte el orden de visita de los clientes que se encuentran entre dos clientes elegidos aleatoriamente. En este caso, todos los clientes deben pertenecer a la misma ruta.
#### Dispersion
Es similar al operador de insercion, pero aplicado a una sub-ruta (conjunto de clientes) en lugar de un unico cliente.
### Busqueda Local (instancias mayores a 500)
El metodo de busqueda consiste en aplicar hasta 50 pasos de busqueda por 1 intercambio, y despues se aplican hasta 50 pasos de 2-opt a cada ruta de la solucion obtenida tras 1 intercambio. El metodo de 1 intercambio consiste en intercambiar un cliente de una ruta por otro perteneciente a otra ruta, o insertar un cliente de una ruta en otra ruta distinta. Por otro lado. 2-opt trabaja siempre dentro de cada ruta, y consiste en eliminar de dos ejes de una ruta y conectar los clientes en la otra forma posible. Como estos dos metodos de busqueda local son deterministas, la busqueda para en el caso de que no se haya logrado mejorar la solucion en un paso del algoritmo. Esto nos permitira reducir considerablemente el tiempo de ejecucion.
