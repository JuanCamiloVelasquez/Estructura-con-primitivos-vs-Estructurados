#include <iostream>
using namespace std;

//=============================================================================
//PARTE 1: Tipo de datos PRIMITIVOS
//=============================================================================
void seccionPrimitivos() {
    cout << "\n======== 1. TIPOS DE DATOS PRIMITIVOS ========" << endl;

    //Cada variable primitiva almacena UN solo valor a la vez
    float notaEstudiante1 = 4.5;
    float notaEstudiante2 = 3.8;
    float notaEstudiante3 = 4.2;
    char grupo            = 'A';
    bool CursoAprobado     = true;

    cout << "Nota estudiante 1: " << notaEstudiante1 << endl;
    cout << "Nota estudiante 2: " << notaEstudiante2 << endl;
    cout << "Nota estudiante 3: " << notaEstudiante3 << endl;
    cout << "Grupo: " << grupo << "| Aprobado: " << CursoAprobado << endl;

    //PROBLEMA A DISCUTIR EN CLASE:
    //Si el curso tiene 40 estudiantes, se necesitarian 40 variables
    //(notaEstudiante1, ..., notaEstudiante40). No es escalable, y no hay 
    //forma de recorrer, buscar o modificar Los datos de forma general
    //con un ciclo cada variable es independiente de las demás.
}

//=============================================================================
//PARTE 2: Tipo de datos ESTRUCTURADOS(arreglo) y sus operaciones
//=============================================================================
const int NUM_ESTUDIANTES_INICIAL = 5;

//Recorrido (traversal): visitar todos los elementos una sola vez
void mostrar(float notas[], int n) {
    cout << "Recorrido ->";
    for (int i = 0; i < n; i++) {
        cout <<notas[i];
        if (i < n - 1) cout << ", ";
    }
    cout << endl;
}

//Busqueda (search): Localizar un valor especifico
int buscar(float notas[], int n, float valor) {
    int comparaciones = 0;
    for (int i = 0; i < n; i++) {
        comparaciones++;
        if (notas[i] == valor) {
            cout << "Encontrada en la posicion: " << i
                 << " (" << comparaciones <<" comparacion(es))" << endl;
            return i;
        }
    }
    cout << "No encontrada tras " << comparaciones <<" comparaciones" << endl;
    return -1;
}

//Insercion (insert): Agregar un nuevo elemento al final
void insertarAlFinal(float notas[], int &n, float valor) {
    notas[n] = valor;
    n++;
}

//eliminacion (delete): remover el elemento en una posicion dada
void eliminarPorPosicion(float notas[], int &n, int pos) {
    for (int i = pos; i < n - 1; i++) {
        notas[i] = notas[i + 1];
    }
    n--;
}

void  seccionEstructurados() {
    cout << "\n======== 2. TIPOS DE DATOS ESTRUCTURADOS (ARREGLO) ========" << endl;

    float notas[10] = {4.5, 3.8, 4.2, 2.9, 3.5};
    int n = NUM_ESTUDIANTES_INICIAL;

    cout << "\n-- Recorrido --" << endl;
    mostrar(notas, n);

    cout << "\n-- Busqueda de la nota 4.2--" << endl;
    buscar(notas, n, 4.2);

    cout << "\n-- Insercion de la nota 3.9 --" << endl;
    insertarAlFinal(notas, n, 3.9);
    mostrar(notas, n);

    cout << "\n-- Eliminacion de la nota en la posicion 1 --" << endl;
    eliminarPorPosicion(notas, n, 1);
    mostrar(notas, n);

    cout << "\n-- Nocion intuitiva de eficiencia --" << endl;
    cout << "Acesso directo notas[0] = " << notas[0] 
         << " -> 1 sola operacion (acesse por indice)" << endl;
    cout << "Buscar un valor recorre, en el pero caso, TODOS los elementos"
         << endl;
}

int main() {
    seccionPrimitivos();
    seccionEstructurados();
    return 0;
}
