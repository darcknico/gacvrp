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
