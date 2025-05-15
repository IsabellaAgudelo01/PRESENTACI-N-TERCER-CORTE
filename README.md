# PRESENTACION-TERCER-CORTE
Isabella Agudelo Rodríguez, Santiago Trujillo Murillo
# Introducción
La librería < deque > en C++ implementa una estructura de datos llamada double-ended queue (cola de doble extremo). Esta estructura permite almacenar y organizar información con la particularidad de que se pueden agregar o eliminar elementos tanto al inicio como al final de la secuencia, lo que le da una gran flexibilidad frente a otras estructuras como < queue > o list.

A diferencia de estas, < deque > ofrece acceso aleatorio rápido y operaciones dinámicas en ambos extremos, lo cual la convierte en una opción eficiente cuando se necesita manipular datos en tiempo real sin sacrificar rendimiento. En este documento se presentarán sus principales funcionalidades, ventajas, desventajas y algunos ejemplos de uso para fortalecer el proceso de aprendizaje en programación con C++.
# Funciones Principales
La librería < deque > incluye diversas funciones que permiten trabajar con los datos de forma versátil. A continuación, se describen las principales y su propósito:

push_back(x): Agrega el valor x al final del deque.

push_front(x): Agrega el valor x al principio del deque.

pop_back(): Elimina el último elemento del deque.

pop_front(): Elimina el primer elemento del deque.

front(): Devuelve el primer elemento sin eliminarlo.

back(): Devuelve el último elemento sin eliminarlo.

size(): Retorna el número total de elementos.

empty(): Indica si el deque está vacío.

at(i): Accede al elemento en la posición i (comenzando desde 0).

Estas funciones permiten un control muy preciso sobre la estructura, ideal para programas que requieren operaciones dinámicas y eficientes.
# Usos comúnes
La estructura < deque > se utiliza frecuentemente en aplicaciones donde se necesita:

1. Procesar datos en tiempo real (por ejemplo, leer datos constantemente y reemplazar los antiguos).

2. Implementar listas de espera o colas con prioridad simple.

3. Controlar historiales de navegación o acciones recientes en un sistema.

4. Simular estructuras complejas donde el orden de entrada y salida de datos es relevante pero cambiante.



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
# Ventajas y desventajas
# _Ventajas_
- Permite insertar y eliminar elementos tanto al principio como al final con alta eficiencia.

- Ofrece acceso directo a cualquier elemento mediante su posición.

- Se ajusta dinámicamente: no requiere definir un tamaño fijo desde el inicio.
# _Desventajas_
- Su manejo interno con bloques de memoria puede hacerla menos eficiente que vector para recorridos largos y repetitivos.

- No incluye funciones integradas para ordenar los datos.

- Algunas operaciones avanzadas que dependen de memoria contigua o punteros directos no son compatibles.

# Conclusión
La librería < deque > es una herramienta muy útil para manejar datos con flexibilidad en ambos extremos de una estructura. Es especialmente práctica en casos donde se requiere modificar el orden de entrada y salida de elementos de forma eficiente. Aunque presenta algunas limitaciones en operaciones muy específicas o recorridos largos, su facilidad de uso y potencia la convierten en una excelente opción para estudiantes que desean avanzar en el manejo de estructuras dinámicas en C++.

El aprendizaje de < deque > no solo permite desarrollar programas más organizados, sino que también ayuda a adquirir una visión más amplia para resolver problemas mediante una mejor gestión de los datos.




