# PRESENTACION-TERCER-CORTE
Isabella Agudelo Rodríguez, Santiago Trujillo Murillo
# Introducción
La librería < deque > es una estructura de datos llamada double-ended queue (cola de doble extremo). Proporciona una forma especial de organizar y guardar información, similar a lo que permiten otras estructuras como < queue > o list, pero con una mayor versatilidad. A diferencia de estas, < deque > ofrece acceso aleatorio rápido y permite realizar operaciones dinámicas tanto al principio como al final de la cola. Si se busca que un programa tenga mayor flexibilidad en el manejo de datos sin sacrificar rendimiento, esta librería es una excelente opción. En este documento se analizarán sus principales funcionalidades, ventajas, desventajas y ejemplos de uso, con el fin de explicar, comprender y aplicar sus conceptos en nuestro proceso de aprendizaje en programación con C++.
# Funciones Principales
Como ya se había mencionado anteriormente, la librería < deque > posee unas funciones y comandos que ayudan a la versatilidad del programa, a continuación se podrá ver la información con el nombre de las funciones y para qué sirven. 

push_back(x): Agrega el número x al final

push_front(x): Agrega el número x al principio

pop_back(): Quita el elemento que está al final

pop_front(): Quita el elemento que está al principio

front(): Devuelve el primer elemento (sin quitarlo)

back(): Devuelve el último elemento (sin quitarlo)

size(): Dice cuántos elementos hay

empty(): Dice si el deque está vacío

at(i): Muestra el elemento que está en la posición i

La librería < deque > es usada genetalmente para casos de procesamiento de datos a tiempo real (por ejemplo si se leen datos y se necesita constantemente eliminar los más antiguos y agregar los nuevos), navegadores, historial, programas donde el orden es esencial y estructuras tipo cola que buscan una flexibilidad extra.

```c++
#include <iostream>
#include <deque>
using namespace std;

int main()
{
    deque<int> numeros; //aquí definimos el deque, funciona parecido a una lista
    numeros.push_back(1);
    numeros.push_back(5);
    numeros.push_front(7);
    cout << "Primer número: " << numeros.front() << endl;
    numeros.pop_front();
    cout << "El número que sigue es: " << numeros.front() << endl;

    return 0;
}
```
