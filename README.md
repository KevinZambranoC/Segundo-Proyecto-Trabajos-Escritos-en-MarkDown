# Segundo-Proyecto-Trabajos-Escritos-en-MarkDown
Es un proyecto didactico en el cual se nos enseña a crear codigo informativo con markdown, y asi documentar de una forma mejor

# Algoritmos de Ordenación Interna 📝

## Prólogo 📖

En el mundo de la informática, la ordenación de datos juega un papel crucial en la eficiencia de muchos sistemas y aplicaciones. Existen varios algoritmos de ordenación interna que permiten organizar datos que residen en la memoria principal, cada uno con sus propias características, ventajas y desventajas. En esta guía, exploraremos algunos de los métodos de ordenación interna más conocidos y utilizados, incluyendo Bubble Sort, Quick Sort, Merge Sort, Insertion Sort, Selection Sort, y Heap Sort. Cada uno de estos algoritmos tiene un enfoque diferente, que varía en eficiencia y aplicabilidad según el caso.

A continuación, se presenta una explicación detallada y ejemplos en C++ de cada uno de estos algoritmos, destacando sus fortalezas, limitaciones y posibles aplicaciones prácticas. 🚀

---

# Bubble Sort ✨

Bubble Sort es uno de los algoritmos de ordenación más simples. Consiste en recorrer la lista repetidamente y comparar elementos adyacentes, intercambiándolos si están en el orden incorrecto. 🔄

**Ventajas** ✅:
- Muy sencillo de implementar. 📝
- Adecuado para listas pequeñas. 📊

**Desventajas** ❌:
- Ineficiente para listas grandes (complejidad O(n²)). 🐢

**Código en C++** 💻:
```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; ++i) {
        for (int j = 0; j < n - i - 1; ++j) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

int main() {
    int arr[] = {64, 25, 12, 22, 11};
    int n = sizeof(arr)/sizeof(arr[0]);
    
    bubbleSort(arr, n);
    
    cout << "Arreglo ordenado: ";
    for (int i = 0; i < n; ++i) {
        cout << arr[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```

**Explicación** 📖:
- El bucle externo controla cuántas veces necesitamos pasar por el arreglo. 🔁
- El bucle interno compara e intercambia los elementos adyacentes si están en el orden incorrecto. ↔️

**Complejidad** ⏱️:
- **Mejor caso**: O(n) - cuando el arreglo ya está ordenado. ✅
- **Promedio y peor caso**: O(n²) - debido a la comparación de todos los elementos. ❌

**Uso Práctico** 🎓:
Bubble Sort se utiliza principalmente con fines educativos debido a su ineficiencia en grandes volúmenes de datos. Es útil para entender conceptos básicos de algoritmos de ordenación. 📚

# Quick Sort 🚀

Quick Sort es un algoritmo de ordenación muy eficiente que sigue el enfoque "divide y vencerás". Selecciona un pivote y divide la lista en dos sublistas, ordenando recursivamente cada una. 🪓

**Ventajas** ✅:
- Muy rápido para listas grandes. ⚡
- Utiliza recursividad, lo que permite una implementación elegante. 🔁

**Desventajas** ❌:
- Puede tener un rendimiento deficiente en listas desbalanceadas (complejidad O(n²)). ⚠️
- Requiere un manejo adecuado del pivote para evitar el peor caso. 🎯

**Código en C++** 💻:
```cpp
#include <iostream>
using namespace std;

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = (low - 1);
    for (int j = low; j < high; ++j) {
        if (arr[j] <= pivot) {
            ++i;
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }
    int temp = arr[i + 1];
    arr[i + 1] = arr[high];
    arr[high] = temp;
    return (i + 1);
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

int main() {
    int arr[] = {10, 7, 8, 9, 1, 5};
    int n = sizeof(arr) / sizeof(arr[0]);
    quickSort(arr, 0, n - 1);
    
    cout << "Arreglo ordenado: ";
    for (int i = 0; i < n; ++i) {
        cout << arr[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```

**Explicación** 📖:
- **Partición**: Elige un elemento como pivote y coloca todos los elementos menores a la izquierda y los mayores a la derecha. 🔄
- **Recursividad**: Quick Sort se llama recursivamente para las sublistas izquierda y derecha del pivote. 🔁

**Complejidad** ⏱️:
- **Mejor caso**: O(n log n) - ocurre cuando el pivote divide las listas de forma balanceada. ✅
- **Promedio**: O(n log n) - generalmente debido a la naturaleza aleatoria de la partición. 📊
- **Peor caso**: O(n²) - cuando el pivote es el elemento más grande o más pequeño (listas desbalanceadas). ❌

**Uso Práctico** 🎓:
Quick Sort es ampliamente utilizado debido a su eficiencia promedio y a su implementación relativamente sencilla. Sin embargo, es importante manejar adecuadamente el pivote para evitar el peor caso. Es muy utilizado en la biblioteca estándar de varios lenguajes. 📚

# Merge Sort 🧩

Merge Sort es un algoritmo de ordenación basado en la técnica "divide y vencerás". Divide la lista en dos mitades, las ordena recursivamente y luego combina (merge) las dos listas ordenadas en una sola. 🔀

**Ventajas** ✅:
- Muy eficiente para listas grandes y para datos que no caben completamente en memoria. 💾
- Siempre tiene una complejidad de O(n log n), sin importar la distribución de los datos. 📊

**Desventajas** ❌:
- Requiere memoria adicional proporcional al tamaño de la lista. 🗂️
- Comparado con otros algoritmos, puede ser más lento en listas pequeñas debido a la sobrecarga de las llamadas recursivas. 🐌

**Código en C++** 💻:
```cpp
#include <iostream>
using namespace std;

void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;
    int L[n1], R[n2];

    for (int i = 0; i < n1; ++i)
        L[i] = arr[left + i];
    for (int j = 0; j < n2; ++j)
        R[j] = arr[mid + 1 + j];

    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            ++i;
        } else {
            arr[k] = R[j];
            ++j;
        }
        ++k;
    }

    while (i < n1) {
        arr[k] = L[i];
        ++i;
        ++k;
    }

    while (j < n2) {
        arr[k] = R[j];
        ++j;
        ++k;
    }
}

void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}

int main() {
    int arr[] = {12, 11, 13, 5, 6, 7};
    int arr_size = sizeof(arr) / sizeof(arr[0]);

    cout << "Arreglo original: ";
    for (int i = 0; i < arr_size; ++i) {
        cout << arr[i] << " ";
    }
    cout << endl;

    mergeSort(arr, 0, arr_size - 1);

    cout << "Arreglo ordenado: ";
    for (int i = 0; i < arr_size; ++i) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

**Explicación** 📖:
- **División**: Divide el arreglo en dos mitades hasta llegar a arreglos de tamaño 1. 🔪
- **Fusión**: Combina las mitades de manera ordenada para formar el arreglo final. 🔄

**Complejidad** ⏱️:
- **Mejor caso**: O(n log n) - debido a la división y fusión continua. ✅
- **Promedio**: O(n log n) - el tiempo requerido es consistente. 📊
- **Peor caso**: O(n log n) - el tiempo sigue siendo O(n log n) sin importar la distribución. ❌

**Uso Práctico** 🎓:
Merge Sort es ideal para trabajar con datos grandes, especialmente cuando se necesita estabilidad en la ordenación. Es comúnmente utilizado en situaciones donde la memoria adicional no es un problema y la eficiencia es crucial. 📚

# Insertion Sort ✍️

Insertion Sort es un algoritmo de ordenación sencillo y eficiente para listas pequeñas. Funciona construyendo la lista ordenada un elemento a la vez, seleccionando cada elemento y ubicándolo en su posición correcta dentro de la parte ya ordenada del arreglo. 📋

**Ventajas** ✅:
- Muy eficiente para listas pequeñas o casi ordenadas. 🚀
- Algoritmo estable que mantiene el orden relativo de los elementos iguales. 🗂️

**Desventajas** ❌:
- Ineficiente para listas grandes (complejidad O(n²)). 🐢
- No es adecuado para grandes volúmenes de datos debido al costo computacional. ⚠️

**Código en C++** 💻:
```cpp
#include <iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; ++i) {
        int key = arr[i];
        int j = i - 1;

        // Mueve los elementos del arreglo que son mayores que la clave un lugar adelante
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            --j;
        }
        arr[j + 1] = key;
    }
}

int main() {
    int arr[] = {12, 11, 13, 5, 6};
    int n = sizeof(arr) / sizeof(arr[0]);

    insertionSort(arr, n);

    cout << "Arreglo ordenado: ";
    for (int i = 0; i < n; ++i) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

**Explicación** 📖:
- **Selección de Clave**: Para cada elemento del arreglo (a partir del segundo), se selecciona como clave (key) y se compara con los elementos anteriores. 🔑
- **Inserción**: Los elementos mayores que la clave se desplazan hacia la derecha para hacer espacio y la clave se inserta en la posición correcta. ➡️

**Complejidad** ⏱️:
- **Mejor caso**: O(n) - ocurre cuando la lista ya está ordenada, ya que solo se realiza una comparación por cada elemento. ✅
- **Promedio y peor caso**: O(n²) - el algoritmo debe comparar e insertar cada elemento en su posición correcta. ❌

**Uso Práctico** 🎓:
Insertion Sort es adecuado para listas pequeñas y cuando se necesita un algoritmo simple y fácil de implementar. También es útil para listas casi ordenadas, donde el tiempo de ejecución tiende a ser cercano a O(n). 📚

# Selection Sort 🎯

Selection Sort es un algoritmo de ordenación sencillo que selecciona repetidamente el elemento más pequeño (o más grande, dependiendo del orden) de la lista no ordenada y lo coloca en la posición correcta. 🔄

**Ventajas** ✅:
- Fácil de entender e implementar. 📝
- No requiere mucha memoria adicional, ya que se realiza en el mismo arreglo. 💾

**Desventajas** ❌:
- Ineficiente para listas grandes (complejidad O(n²)). 🐢
- No es un algoritmo estable, ya que el orden relativo de los elementos iguales no se mantiene. ⚠️

**Código en C++** 💻:
```cpp
#include <iostream>
using namespace std;

void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; ++i) {
        int minIndex = i;
        for (int j = i + 1; j < n; ++j) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        // Intercambiar el elemento mínimo encontrado con el primer elemento
        int temp = arr[minIndex];
        arr[minIndex] = arr[i];
        arr[i] = temp;
    }
}

int main() {
    int arr[] = {64, 25, 12, 22, 11};
    int n = sizeof(arr) / sizeof(arr[0]);

    selectionSort(arr, n);

    cout << "Arreglo ordenado: ";
    for (int i = 0; i < n; ++i) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

**Explicación** 📖:
- **Selección del Mínimo**: Para cada posición del arreglo, se busca el elemento más pequeño en la parte no ordenada y se coloca en la posición correcta. 🔍
- **Intercambio**: Se intercambia el elemento más pequeño encontrado con el primer elemento de la parte no ordenada. ↔️

**Complejidad** ⏱️:
- **Mejor, promedio y peor caso**: O(n²) - en todos los casos, se realizan comparaciones para cada elemento del arreglo. ❌

**Uso Práctico** 🎓:
Selection Sort se utiliza principalmente cuando se requiere una implementación sencilla para listas pequeñas. No es adecuado para listas grandes debido a su ineficiencia, pero es útil para enseñar los conceptos básicos de algoritmos de ordenación. 📚

# Heap Sort ⛰️

Heap Sort es un algoritmo de ordenación basado en la estructura de datos llamada "heap". Utiliza un árbol binario de máxima o mínima (max-heap o min-heap) para ordenar los elementos. Primero se construye un heap a partir del arreglo y luego se extrae el elemento raíz repetidamente para construir el arreglo ordenado. 🌳

**Ventajas** ✅:
- Tiene una complejidad O(n log n) en el peor caso, lo cual lo hace eficiente para grandes volúmenes de datos. 📊
- No requiere memoria adicional significativa (a diferencia de Merge Sort). 💾

**Desventajas** ❌:
- No es un algoritmo estable, lo que significa que no preserva el orden relativo de los elementos iguales. ⚠️
- Puede ser más lento en comparación con Quick Sort debido a las operaciones de mantenimiento del heap. 🐢

**Código en C++** 💻:
```cpp
#include <iostream>
using namespace std;

void heapify(int arr[], int n, int i) {
    int largest = i; // Inicializar el nodo más grande como raíz
    int left = 2 * i + 1; // Hijo izquierdo
    int right = 2 * i + 2; // Hijo derecho

    // Si el hijo izquierdo es más grande que la raíz
    if (left < n && arr[left] > arr[largest])
        largest = left;

    // Si el hijo derecho es más grande que el más grande hasta ahora
    if (right < n && arr[right] > arr[largest])
        largest = right;

    // Si el más grande no es la raíz
    if (largest != i) {
        swap(arr[i], arr[largest]);
        // Recursivamente aplicar heapify al subárbol afectado
        heapify(arr, n, largest);
    }
}

void heapSort(int arr[], int n) {
    // Construir el heap (reorganizar el arreglo)
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    // Extraer uno por uno los elementos del heap
    for (int i = n - 1; i > 0; i--) {
        // Mover la raíz actual al final
        swap(arr[0], arr[i]);
        // Llamar a heapify en el heap reducido
        heapify(arr, i, 0);
    }
}

int main() {
    int arr[] = {12, 11, 13, 5, 6, 7};
    int n = sizeof(arr) / sizeof(arr[0]);

    heapSort(arr, n);

    cout << "Arreglo ordenado: ";
    for (int i = 0; i < n; ++i) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

**Explicación** 📖:
- **Construcción del Heap**: Primero se reorganiza el arreglo para convertirlo en un max-heap. Esto asegura que el elemento más grande esté en la raíz. 🌲
- **Extracción y Heapify**: Se extrae el elemento de la raíz (máximo) y se coloca al final del arreglo. Luego se llama a `heapify` para restaurar la propiedad del heap. 🔄

**Complejidad** ⏱️:
- **Mejor, promedio y peor caso**: O(n log n) - debido a la necesidad de mantener la estructura del heap. ✅

**Uso Práctico** 🎓:
Heap Sort se utiliza en sistemas embebidos y en situaciones donde el peor caso de tiempo de ejecución debe ser garantizado. También se usa cuando se requiere un algoritmo de ordenación eficiente sin requerir espacio adicional significativo. 📚






