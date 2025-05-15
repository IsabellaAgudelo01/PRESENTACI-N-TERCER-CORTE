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

# Ejemplos
_Ejemplo 1_
```c++
#include <iostream>
#include <deque>
using namespace std;

int main()
{
    deque<int> numeros; //definimos el deque
    //insertamos los elementos
    numeros.push_back(1); // [1]
    numeros.push_back(5); // [1,, 5]
    numeros.push_front(7); // [7, 1, 5]
    cout << "Primer número: " << numeros.front() << endl;
    numeros.pop_front();
    cout << "El número que sigue es: " << numeros.front() << endl;
    numeros.pop_front();
    cout << "El número faltante es: " << numeros.front();
    return 0;
}
```
_Ejemplo 2_

```c++
#include <iostream>
#include <deque>
using namespace std;

int main()
{
    deque<int> numeros; // definimos el deque
    // asignamos los elementos
    numeros.push_front(40); // [40]
    numeros.push_back(60); // [40, 60]
    numeros.push_front(70); // [70, 40, 60]
    numeros.push_back(30); // [70, 40, 60, 30]
    
    cout << "contenido del deque: ";
    for (int i = 0; i < numeros.size(); i++){
        cout << numeros.at(i) << " ";
    }
    cout << endl;
    numeros.pop_front(); //elimina 70
    numeros.pop_back(); //elimina 30
    cout << "Después de eliminar los extremos: ";
    for (int i = 0; i < numeros.size(); i++){
        cout << numeros.at(i) << " ";
    }
    return 0;
}
```
_Ejemplo 3_
```c++
#include <iostream>
#include <deque>
using namespace std;

int main(){
    deque<int> lista;
    int o;
    //bucle principal del programa
    while (true) { 
        cout << "Sistema de vacunación\n";
        cout << "1. Registrar persona\n";
        cout << "2. Atender siguiente persona en la lista\n";
        cout << "3. Ver lista de espera\n";
        cout << "4. Salir\n";
        cout << "Elige una opción: ";
        cin >> o;
        if (o==1){
            int e;
            cout << "Ingrese la edad de la persona: ";
            cin >> e;
            if (e>60){
                //Persona mayor a 60 con prioridad
                lista.push_front(e); //se agrega al inicio de la lista
                cout << "Persona con prioridad agregada a la lista de espera\n";
            } else {
                lista.push_back(e); //en caso de ser menor a 60 se agrega al final de la lista
                cout << "Persona sin prioridad agregada a la lista de espera\n";
            }
        } else if (o==2){
            if(lista.empty()){
                cout << "No hay personas en la lista\n";
            } else {
                cout << "Atendiendo persona de " << lista.front() << " años\n"; //mostrar persona al inicio de la lista
                lista.pop_front(); //quitar persona al inicio de la lista
            }
        } else if (o==3){
            if(lista.empty()){
                cout << "La lista está vacía\n";
            } else {
                cout << "Personas en la lista de espera (en orden de prioridad):\n";
                for (int i = 0; i < lista.size(); i++){
                    //mostrar cada persona de la lista con su posición
                    cout << i + 1 << ". Edad: " << lista.at(i) << endl;
                    if (lista.at(i) > 60) {
                        //mostrar si tiene prioridad
                        cout << " (Prioridad)";
                    }
                    cout << endl;
                }
            }
        } else if (o>4){
            cout << "Opción inválida\n";
        } else {
            cout << "Saliendo del programa...";
            break;
        }
    }
    return 0;
}
```




