# Segundo-Proyecto-Trabajos-Escritos-en-MarkDown
Es un proyecto didactico en el cual se nos enseña a crear codigo informativo con markdown, y asi documentar de una forma mejor

# 1. Algoritmos de Ordenación Interna 📝

En el mundo de la informática, la ordenación de datos juega un papel crucial en la eficiencia de muchos sistemas y aplicaciones. Existen varios algoritmos de ordenación interna que permiten organizar datos que residen en la memoria principal, cada uno con sus propias características, ventajas y desventajas. En esta guía, exploraremos algunos de los métodos de ordenación interna más conocidos y utilizados, incluyendo Bubble Sort, Quick Sort, Merge Sort, Insertion Sort, Selection Sort, y Heap Sort. Cada uno de estos algoritmos tiene un enfoque diferente, que varía en eficiencia y aplicabilidad según el caso.

A continuación, se presenta una lista con todos los metodos de ordenación interna y luego una explicación detallada y ejemplos en C++ de cada uno de estos algoritmos, destacando sus fortalezas, limitaciones y posibles aplicaciones prácticas. 🚀

## Métodos de Ordenación Interna 📋
1. **Bubble Sort** ✨
2. **Quick Sort** 🚀
3. **Merge Sort** 🧩
4. **Insertion Sort** ✍️
5. **Selection Sort** 🎯
6. **Heap Sort** ⛰️
---

# 1. 1. Bubble Sort ✨

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

# 1. 2. Quick Sort 🚀

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

# 1. 3. Merge Sort 🧩

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

# 1. 4. Insertion Sort ✍️

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

# 1. 5. Selection Sort 🎯

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

# 1. 6. Heap Sort ⛰️

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

# 2. Algoritmos de Ordenación Externa 📦

Los algoritmos de ordenación externa se utilizan para ordenar grandes volúmenes de datos que no caben completamente en la memoria principal. Estos datos se encuentran almacenados en dispositivos de almacenamiento secundarios, como discos duros. La ordenación externa se realiza dividiendo los datos en partes más pequeñas que pueden ser procesadas en memoria y luego combinando los resultados de forma eficiente. En esta sección, exploraremos algunos de los métodos más comunes de ordenación externa, como el Merge Sort Externo, Polyphase Merge Sort, y la Ordenación por Mezcla en Varios Pasos. 📂

---

## Métodos de Ordenación Externa 📋
1. **Merge Sort Externo** 🧩
2. **Polyphase Merge Sort** 🔄
3. **Ordenación por Mezcla en Varios Pasos** 🌐

# 2. 1. Merge Sort Externo 🧩

El Merge Sort Externo es una técnica utilizada para ordenar grandes volúmenes de datos que se encuentran almacenados en dispositivos externos. Se basa en dividir los datos en partes más pequeñas que pueden ser ordenadas en la memoria principal y luego fusionarlas de manera eficiente. Este enfoque minimiza la cantidad de lecturas y escrituras en el disco, lo cual es crucial para lograr un buen rendimiento. 🚀

**Ventajas** ✅:
- Complejidad O(n log n) en el peor caso, lo que garantiza un buen rendimiento. ⚡
- Ideal para ordenar archivos muy grandes que no pueden cargarse completamente en memoria. 📂

**Desventajas** ❌:
- Requiere espacio adicional en disco para almacenar los subarchivos temporales. 📂
- Puede ser más lento que otros métodos de ordenación interna debido a los múltiples accesos al disco. 🐢

**Código en C++** 💻:
```cpp
#include <iostream>
#include <fstream>
#include <vector>
#include <algorithm>
using namespace std;

void dividirArchivo(const string& nombreArchivo, int tamanioBloque) {
    ifstream archivoEntrada(nombreArchivo, ios::binary);
    if (!archivoEntrada.is_open()) {
        cout << "No se pudo abrir el archivo." << endl;
        return;
    }

    vector<int> buffer(tamanioBloque);
    int contador = 0;

    while (!archivoEntrada.eof()) {
        archivoEntrada.read(reinterpret_cast<char*>(buffer.data()), tamanioBloque * sizeof(int));
        streamsize elementosLeidos = archivoEntrada.gcount() / sizeof(int);

        if (elementosLeidos == 0) break;

        sort(buffer.begin(), buffer.begin() + elementosLeidos);

        ofstream archivoSalida("subarchivo_" + to_string(contador++) + ".bin", ios::binary);
        archivoSalida.write(reinterpret_cast<char*>(buffer.data()), elementosLeidos * sizeof(int));
        archivoSalida.close();
    }

    archivoEntrada.close();
}

int main() {
    string nombreArchivo = "datos_grandes.bin";
    int tamanioBloque = 100; // Número de elementos que se pueden cargar en memoria

    dividirArchivo(nombreArchivo, tamanioBloque);

    return 0;
}
```
# 2. 2. Polyphase Merge Sort 🔄

El Polyphase Merge Sort es una variación del Merge Sort diseñada para optimizar el proceso de fusión en la ordenación externa. Utiliza múltiples archivos temporales para minimizar el número de fusiones y lecturas/escrituras necesarias, lo cual es especialmente beneficioso cuando se trabaja con almacenamiento secundario. 🌀

**Ventajas** ✅:
- Reduce el número de pasadas y fusiones al usar múltiples subarchivos. 📉
- Minimiza la cantidad de espacio adicional requerido en comparación con otras técnicas de fusión. 💾

**Desventajas** ❌:
- La implementación es más compleja que el Merge Sort Externo estándar. ⚠️
- Requiere un cálculo cuidadoso de la distribución de subarchivos para maximizar la eficiencia. 📊

**Código en C++** 💻:
```cpp
#include <iostream>
#include <fstream>
#include <vector>
#include <queue>
using namespace std;

struct NodoArchivo {
    int valor;
    int indexArchivo;

    bool operator<(const NodoArchivo& otro) const {
        return valor > otro.valor;
    }
};

void polyphaseMergeSort(const vector<string>& subarchivos, const string& archivoFinal) {
    priority_queue<NodoArchivo> minHeap;
    vector<ifstream> archivosEntrada(subarchivos.size());

    // Abrir todos los archivos de subarchivos
    for (int i = 0; i < subarchivos.size(); ++i) {
        archivosEntrada[i].open(subarchivos[i], ios::binary);
        if (archivosEntrada[i].is_open()) {
            int valor;
            archivosEntrada[i].read(reinterpret_cast<char*>(&valor), sizeof(valor));
            if (!archivosEntrada[i].eof()) {
                minHeap.push({valor, i});
            }
        }
    }

    ofstream archivoSalida(archivoFinal, ios::binary);

    // Fusión de todos los subarchivos
    while (!minHeap.empty()) {
        NodoArchivo actual = minHeap.top();
        minHeap.pop();
        archivoSalida.write(reinterpret_cast<char*>(&actual.valor), sizeof(actual.valor));

        int indexArchivo = actual.indexArchivo;
        int valor;
        archivosEntrada[indexArchivo].read(reinterpret_cast<char*>(&valor), sizeof(valor));
        if (!archivosEntrada[indexArchivo].eof()) {
            minHeap.push({valor, indexArchivo});
        }
    }

    // Cerrar todos los archivos
    for (auto& archivo : archivosEntrada) {
        archivo.close();
    }
    archivoSalida.close();
}

int main() {
    vector<string> subarchivos = {"subarchivo_0.bin", "subarchivo_1.bin", "subarchivo_2.bin"};
    string archivoFinal = "datos_ordenados.bin";

    polyphaseMergeSort(subarchivos, archivoFinal);

    return 0;
}
```
# 2. 3. Ordenación por Mezcla en Varios Pasos 🌐

La Ordenación por Mezcla en Varios Pasos (Multi-way Merge Sort) es una técnica que extiende el concepto de fusión a más de dos subarchivos a la vez. En lugar de fusionar dos archivos en cada paso, este método permite fusionar múltiples subarchivos simultáneamente, lo cual reduce el número de pasos necesarios para completar la ordenación. Esta técnica es especialmente útil para reducir el número de accesos a disco y mejorar el rendimiento en la ordenación de grandes volúmenes de datos. 🚀

**Ventajas** ✅:
- Reduce significativamente el número de pasadas necesarias para fusionar todos los subarchivos. 📉
- Es más eficiente para conjuntos de datos extremadamente grandes, ya que disminuye la cantidad de accesos a disco. 💾

**Desventajas** ❌:
- Requiere una mayor cantidad de memoria para mantener los múltiples subarchivos en el proceso de fusión. ⚠️
- La complejidad de implementación aumenta al manejar múltiples subarchivos simultáneamente. 📊

**Código en C++** 💻:
```cpp
#include <iostream>
#include <fstream>
#include <vector>
#include <queue>
using namespace std;

struct NodoArchivo {
    int valor;
    int indexArchivo;

    bool operator<(const NodoArchivo& otro) const {
        return valor > otro.valor;
    }
};

void multiWayMergeSort(const vector<string>& subarchivos, const string& archivoFinal) {
    priority_queue<NodoArchivo> minHeap;
    vector<ifstream> archivosEntrada(subarchivos.size());

    // Abrir todos los archivos de subarchivos
    for (int i = 0; i < subarchivos.size(); ++i) {
        archivosEntrada[i].open(subarchivos[i], ios::binary);
        if (archivosEntrada[i].is_open()) {
            int valor;
            archivosEntrada[i].read(reinterpret_cast<char*>(&valor), sizeof(valor));
            if (!archivosEntrada[i].eof()) {
                minHeap.push({valor, i});
            }
        }
    }

    ofstream archivoSalida(archivoFinal, ios::binary);

    // Fusión de todos los subarchivos
    while (!minHeap.empty()) {
        NodoArchivo actual = minHeap.top();
        minHeap.pop();
        archivoSalida.write(reinterpret_cast<char*>(&actual.valor), sizeof(actual.valor));

        int indexArchivo = actual.indexArchivo;
        int valor;
        archivosEntrada[indexArchivo].read(reinterpret_cast<char*>(&valor), sizeof(valor));
        if (!archivosEntrada[indexArchivo].eof()) {
            minHeap.push({valor, indexArchivo});
        }
    }

    // Cerrar todos los archivos
    for (auto& archivo : archivosEntrada) {
        archivo.close();
    }
    archivoSalida.close();
}

int main() {
    vector<string> subarchivos = {"subarchivo_0.bin", "subarchivo_1.bin", "subarchivo_2.bin"};
    string archivoFinal = "datos_ordenados.bin";

    multiWayMergeSort(subarchivos, archivoFinal);

    return 0;
}
```

**Explicación** 📖:
- **Fusión con Min-Heap**: Utiliza un min-heap para fusionar los elementos más pequeños de cada subarchivo, manteniendo el orden ascendente en el archivo final. 🔄
- **Uso de Múltiples Subarchivos**: Se abren y leen varios subarchivos simultáneamente para minimizar el número de pasadas necesarias. 📂

**Complejidad** ⏱️:
- **Complejidad**: O(n log k) - donde k es el número de subarchivos. 📊

**Uso Práctico** 🎓:
La Ordenación por Mezcla en Varios Pasos se utiliza cuando se necesita manejar grandes volúmenes de datos almacenados externamente, ya que mejora el rendimiento y minimiza los accesos a disco. Es comúnmente utilizada en la clasificación de registros en bases de datos y aplicaciones que trabajan con almacenamiento masivo. 📚


# 3. Algoritmos de Búsqueda Interna 🔍

Los algoritmos de búsqueda interna permiten localizar elementos dentro de una estructura de datos almacenada en la memoria principal. Estos algoritmos son fundamentales para optimizar el acceso y la manipulación de datos en sistemas de software. En esta sección, exploraremos algunos de los métodos de búsqueda interna más comunes, como la Búsqueda Secuencial, la Búsqueda Binaria, y el Hashing. Cada uno tiene sus propias ventajas y limitaciones, dependiendo del tipo de datos y la situación específica. 🔄

---
# Algoritmos de Búsqueda 📂

## Métodos de Búsqueda Interna 🔍
1. **Búsqueda Secuencial** 🔄
2. **Búsqueda Binaria Interno** ⚡
3. **Hashing Interno** 🔑

# 3. 1. Búsqueda Secuencial 🔄

La Búsqueda Secuencial es uno de los algoritmos más simples para buscar un elemento en una lista. Se recorre cada elemento uno por uno hasta encontrar el valor deseado o hasta que se hayan revisado todos los elementos. Es especialmente útil para listas pequeñas o cuando los datos no están ordenados. 🔄

**Ventajas** ✅:
- Muy simple de implementar y entender. 📝
- No requiere que los datos estén ordenados. 📋

**Desventajas** ❌:
- Ineficiente para listas grandes debido a la complejidad O(n). 🐢
- Poco práctico si se realizan múltiples búsquedas en grandes volúmenes de datos. ⚠️

**Código en C++** 💻:
```cpp
#include <iostream>
using namespace std;

int busquedaSecuencial(int arr[], int n, int x) {
    for (int i = 0; i < n; ++i) {
        if (arr[i] == x) {
            return i; // Retorna el índice donde se encuentra el elemento
        }
    }
    return -1; // Retorna -1 si no se encuentra el elemento
}

int main() {
    int arr[] = {2, 3, 4, 10, 40};
    int x = 10;
    int n = sizeof(arr) / sizeof(arr[0]);

    int resultado = busquedaSecuencial(arr, n, x);
    if (resultado == -1)
        cout << "Elemento no está presente en el arreglo.";
    else
        cout << "Elemento encontrado en el índice: " << resultado;

    return 0;
}
```

**Explicación** 📖:
- **Recorrido Secuencial**: Se recorre el arreglo desde el primer elemento hasta el último, comparando cada uno con el valor buscado. 🔄
- **Resultado**: Si se encuentra el elemento, se devuelve su índice; si no se encuentra, se devuelve -1. ❌

**Complejidad** ⏱️:
- **Mejor caso**: O(1) - si el elemento se encuentra en la primera posición. ✅
- **Promedio y peor caso**: O(n) - en el peor caso, se debe recorrer toda la lista. ❌

**Uso Práctico** 🎓:
La Búsqueda Secuencial se utiliza en listas pequeñas o en casos donde la eficiencia no es crítica. Es útil para aprender los conceptos básicos de algoritmos de búsqueda y cuando los datos no están ordenados. 📚

# 3. 2. Búsqueda Binaria Interna ⚡

La Búsqueda Binaria es un algoritmo eficiente para buscar un elemento en una lista ordenada. Se basa en dividir repetidamente el rango de búsqueda a la mitad, comparando el valor buscado con el elemento del medio del rango. Este enfoque permite encontrar el valor deseado con una complejidad logarítmica. ➗

**Ventajas** ✅:
- Muy eficiente para listas grandes, con una complejidad de O(log n). ⚡
- Reduce drásticamente el número de comparaciones necesarias. 🔽

**Desventajas** ❌:
- Solo funciona con listas que están previamente ordenadas. 📋
- Requiere un control cuidadoso del rango de búsqueda, lo que puede hacer que sea más difícil de implementar que la búsqueda secuencial. 🧩

**Código en C++** 💻:
```cpp
#include <iostream>
using namespace std;

int busquedaBinaria(int arr[], int izquierda, int derecha, int x) {
    while (izquierda <= derecha) {
        int medio = izquierda + (derecha - izquierda) / 2;

        // Verificar si el elemento está en la mitad
        if (arr[medio] == x)
            return medio;

        // Si el elemento es mayor, ignorar la mitad izquierda
        if (arr[medio] < x)
            izquierda = medio + 1;

        // Si el elemento es menor, ignorar la mitad derecha
        else
            derecha = medio - 1;
    }

    // Si el elemento no está presente en el arreglo
    return -1;
}

int main() {
    int arr[] = {2, 3, 4, 10, 40};
    int x = 10;
    int n = sizeof(arr) / sizeof(arr[0]);

    int resultado = busquedaBinaria(arr, 0, n - 1, x);
    if (resultado == -1)
        cout << "Elemento no está presente en el arreglo.";
    else
        cout << "Elemento encontrado en el índice: " << resultado;

    return 0;
}
```

**Explicación** 📖:
- **División del Rango**: Cada vez se calcula el elemento medio del rango actual y se compara con el valor buscado. 🔄
- **Actualización del Rango**: Si el valor buscado es mayor, se mueve el rango hacia la derecha; si es menor, hacia la izquierda. ➡️⬅️

**Complejidad** ⏱️:
- **Mejor caso**: O(1) - si el elemento se encuentra en la mitad del rango inicial. ✅
- **Promedio y peor caso**: O(log n) - el rango se reduce a la mitad en cada paso. 📊

**Uso Práctico** 🎓:
La Búsqueda Binaria se utiliza comúnmente cuando se requiere un algoritmo rápido y eficiente para listas ordenadas. Se emplea en muchas aplicaciones, como bases de datos y sistemas de búsqueda, para optimizar la localización de información. 📚

# 3. 3. Hashing Interno 🔑

El Hashing es una técnica utilizada para almacenar y buscar datos de manera extremadamente rápida. Consiste en convertir una clave (key) en una posición dentro de una tabla, conocida como tabla hash, utilizando una función hash. Este enfoque permite acceder a los datos en un tiempo constante, O(1), en el mejor de los casos. 🔒

**Ventajas** ✅:
- Acceso muy rápido a los datos, con una complejidad promedio de O(1). ⚡
- Ideal para grandes volúmenes de datos, donde se necesita acceder rápidamente. 📊

**Desventajas** ❌:
- Puede haber colisiones, donde dos claves distintas se mapean a la misma posición. ⚠️
- Requiere una buena función hash para minimizar las colisiones y lograr una distribución uniforme. 🔄

**Código en C++** 💻:
```cpp
#include <iostream>
#include <list>
using namespace std;

class HashTable {
private:
    int numBuckets; // Número de cubetas
    list<int> *tabla; // Apuntador a una lista que contiene los buckets

public:
    HashTable(int V);
    void insertarElemento(int clave);
    void eliminarElemento(int clave);
    int funcionHash(int clave) {
        return clave % numBuckets;
    }
    void mostrarTabla();
};

HashTable::HashTable(int b) {
    this->numBuckets = b;
    tabla = new list<int>[numBuckets];
}

void HashTable::insertarElemento(int clave) {
    int indice = funcionHash(clave);
    tabla[indice].push_back(clave);
}

void HashTable::eliminarElemento(int clave) {
    int indice = funcionHash(clave);
    list<int>::iterator it;
    for (it = tabla[indice].begin(); it != tabla[indice].end(); ++it) {
        if (*it == clave) {
            tabla[indice].erase(it);
            break;
        }
    }
}

void HashTable::mostrarTabla() {
    for (int i = 0; i < numBuckets; ++i) {
        cout << i;
        for (auto x : tabla[i])
            cout << " --> " << x;
        cout << endl;
    }
}

int main() {
    int claves[] = {15, 11, 27, 8, 12};
    int n = sizeof(claves) / sizeof(claves[0]);

    HashTable tablaHash(7); // Tabla hash con 7 buckets
    for (int i = 0; i < n; ++i)
        tablaHash.insertarElemento(claves[i]);

    tablaHash.mostrarTabla();

    tablaHash.eliminarElemento(12);
    cout << "\nDespués de eliminar 12:\n";
    tablaHash.mostrarTabla();

    return 0;
}
```

**Explicación** 📖:
- **Función Hash**: La función hash mapea cada clave a una posición en la tabla hash (bucket). 🔄
- **Colisiones**: Cuando dos claves diferentes se mapean al mismo bucket, se almacenan juntas en una lista vinculada (chaining). ⚔️
- **Operaciones Básicas**: El algoritmo permite insertar, eliminar y buscar elementos en la tabla hash con una eficiencia muy alta. ✅

**Complejidad** ⏱️:
- **Mejor caso**: O(1) - cuando no hay colisiones y la función hash distribuye bien los elementos. 🚀
- **Peor caso**: O(n) - cuando hay muchas colisiones y todos los elementos se almacenan en el mismo bucket. ❌

**Uso Práctico** 🎓:
El Hashing se utiliza en bases de datos, estructuras de datos dinámicas como los diccionarios en Python, y en aplicaciones donde el acceso rápido a los datos es crucial, como el almacenamiento en caché y la búsqueda de contraseñas. 📚

# 4. Algoritmos de Búsqueda Externa 📂

Los algoritmos de búsqueda externa se utilizan para buscar datos que no se encuentran completamente en la memoria principal, sino en dispositivos de almacenamiento secundarios, como discos duros o bases de datos. Estos métodos son cruciales para trabajar con grandes volúmenes de información que no pueden ser cargados directamente en la memoria. En esta sección, exploraremos varios métodos de búsqueda externa, como la búsqueda secuencial simple, secuencial indexada, binaria y hashing externo. 📁

## Métodos de Búsqueda Externa 📂
1. **Búsqueda Secuencial Simple** 📜
2. **Búsqueda Secuencial Indexada o por Bloques** 🧱
3. **Búsqueda Binaria Externa** 🌲
4. **Hashing Externo** 🔐

# 4. 1. Búsqueda Secuencial Simple 📜

La Búsqueda Secuencial Simple es un método utilizado para buscar datos almacenados en dispositivos de almacenamiento externo, como discos duros. Al igual que la búsqueda secuencial interna, se recorren los datos uno por uno hasta encontrar el valor deseado. Este método es muy útil cuando los datos no están en memoria principal y se almacenan en archivos secuenciales. 🗄️

**Ventajas** ✅:
- Fácil de implementar y entender. 📝
- No requiere que los datos estén ordenados. 📋

**Desventajas** ❌:
- Es ineficiente para grandes volúmenes de datos, con una complejidad O(n). 🐢
- Puede resultar lento debido a los tiempos de acceso a disco. ⚠️

**Código en C++** 💻:
```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

void busquedaSecuencialArchivo(const string& nombreArchivo, int clave) {
    ifstream archivo(nombreArchivo);
    if (!archivo.is_open()) {
        cout << "No se pudo abrir el archivo." << endl;
        return;
    }

    int dato;
    bool encontrado = false;
    while (archivo >> dato) {
        if (dato == clave) {
            encontrado = true;
            break;
        }
    }

    archivo.close();

    if (encontrado) {
        cout << "Elemento " << clave << " encontrado en el archivo." << endl;
    } else {
        cout << "Elemento " << clave << " no encontrado en el archivo." << endl;
    }
}

int main() {
    string nombreArchivo = "datos.txt";
    int clave = 27;

    busquedaSecuencialArchivo(nombreArchivo, clave);

    return 0;
}
```

**Explicación** 📖:
- **Apertura del Archivo**: El archivo se abre para ser leído, y si no se puede abrir, se muestra un mensaje de error. 📂
- **Recorrido Secuencial**: Se recorren todos los elementos en el archivo uno por uno hasta encontrar el valor buscado. 🔄
- **Cierre del Archivo**: Una vez terminada la búsqueda, se cierra el archivo para liberar los recursos. ✅

**Complejidad** ⏱️:
- **Mejor caso**: O(1) - si el elemento buscado es el primero en el archivo. 🚀
- **Promedio y peor caso**: O(n) - en el peor caso, se deben recorrer todos los elementos. ❌

**Uso Práctico** 🎓:
La Búsqueda Secuencial Simple es útil para trabajar con archivos pequeños que no están en memoria principal y que no están ordenados. Su implementación es sencilla y no requiere estructuras de datos complicadas. Es útil para búsquedas en archivos de registros pequeños o de pruebas. 📚

# 4. 2. Búsqueda Secuencial Indexada o por Bloques  🧱

La Búsqueda Secuencial Indexada es un método de búsqueda externa que combina una estructura de índice con la búsqueda secuencial. Se utiliza para mejorar la eficiencia de la búsqueda en grandes archivos externos. La búsqueda comienza con el índice para reducir el rango de búsqueda y luego se realiza una búsqueda secuencial dentro del bloque seleccionado. 📊

**Ventajas** ✅:
- Reduce significativamente el número de elementos a buscar mediante el uso de un índice. 📉
- Mejora el rendimiento respecto a la búsqueda secuencial simple, especialmente para archivos grandes. ⚡

**Desventajas** ❌:
- Requiere espacio adicional para almacenar el índice. 📂
- La eficiencia depende de cómo se diseñe el índice; un mal diseño puede reducir la efectividad. ⚠️

**Código en C++** 💻:
```cpp
#include <iostream>
#include <fstream>
#include <vector>
using namespace std;

struct Indice {
    int clave;
    long posicion; // Posición en el archivo
};

void busquedaSecuencialIndexada(const string& nombreArchivo, const vector<Indice>& indices, int clave) {
    ifstream archivo(nombreArchivo, ios::binary);
    if (!archivo.is_open()) {
        cout << "No se pudo abrir el archivo." << endl;
        return;
    }

    // Buscar en el índice para reducir el rango de búsqueda
    long inicio = -1;
    for (const auto& idx : indices) {
        if (idx.clave > clave) {
            break;
        }
        inicio = idx.posicion;
    }

    if (inicio == -1) {
        cout << "Elemento " << clave << " no encontrado en el archivo." << endl;
        archivo.close();
        return;
    }

    // Realizar búsqueda secuencial en el bloque identificado
    archivo.seekg(inicio, ios::beg);
    int dato;
    while (archivo.read(reinterpret_cast<char*>(&dato), sizeof(dato))) {
        if (dato == clave) {
            cout << "Elemento " << clave << " encontrado en el archivo." << endl;
            archivo.close();
            return;
        }
        if (dato > clave) { // Si el dato es mayor, ya no se encontrará el elemento
            break;
        }
    }

    archivo.close();
    cout << "Elemento " << clave << " no encontrado en el archivo." << endl;
}

int main() {
    // Índice simulado (en una aplicación real, se generaría previamente)
    vector<Indice> indices = {{5, 0}, {15, 20}, {25, 40}, {35, 60}};
    string nombreArchivo = "datos.bin";
    int clave = 25;

    busquedaSecuencialIndexada(nombreArchivo, indices, clave);

    return 0;
}
```

**Explicación** 📖:
- **Uso del Índice**: Se utiliza un índice que contiene pares de clave y posición para reducir el rango de búsqueda al bloque correcto. 📌
- **Búsqueda Secuencial en el Bloque**: Una vez encontrado el bloque, se realiza una búsqueda secuencial dentro de ese bloque específico. 🔍

**Complejidad** ⏱️:
- **Mejor caso**: O(1) - si el índice lleva directamente al elemento deseado. 🚀
- **Promedio y peor caso**: O(n/m) + O(m) - depende del tamaño del índice (n/m es la búsqueda en el índice y m es la búsqueda en el bloque). ❌

**Uso Práctico** 🎓:
La Búsqueda Secuencial Indexada se utiliza en sistemas de bases de datos y archivos muy grandes, donde la búsqueda secuencial simple sería demasiado lenta. Esta técnica permite limitar la cantidad de lecturas al usar un índice que localiza los registros de forma más rápida. 📚

# 4. 3. Búsqueda Binaria Externa 🌲

La Búsqueda Binaria Externa es una técnica que se utiliza cuando los datos están almacenados en dispositivos externos y están organizados de forma ordenada. Similar a la búsqueda binaria interna, esta técnica divide repetidamente el conjunto de datos en dos partes para localizar el valor buscado. Es particularmente eficiente para grandes volúmenes de datos almacenados en discos duros o bases de datos. 📊

**Ventajas** ✅:
- Alta eficiencia con complejidad O(log n) al trabajar con archivos grandes que están ordenados. ⚡
- Reduce significativamente el número de accesos al disco, mejorando el rendimiento de la búsqueda. 📉

**Desventajas** ❌:
- Solo se aplica a archivos que ya están ordenados. 📋
- Requiere más control en la gestión de los accesos a disco, lo que puede complicar la implementación. ⚠️

**Código en C++** 💻:
```cpp
#include <iostream>
#include <fstream>
using namespace std;

long busquedaBinariaArchivo(const string& nombreArchivo, int clave) {
    ifstream archivo(nombreArchivo, ios::binary);
    if (!archivo.is_open()) {
        cout << "No se pudo abrir el archivo." << endl;
        return -1;
    }

    archivo.seekg(0, ios::end);
    long tamanoArchivo = archivo.tellg();
    long numElementos = tamanoArchivo / sizeof(int);

    long izquierda = 0, derecha = numElementos - 1;
    int dato;

    while (izquierda <= derecha) {
        long medio = izquierda + (derecha - izquierda) / 2;
        archivo.seekg(medio * sizeof(int), ios::beg);
        archivo.read(reinterpret_cast<char*>(&dato), sizeof(dato));

        if (dato == clave) {
            archivo.close();
            return medio; // Retorna la posición del elemento encontrado
        }

        if (dato < clave) {
            izquierda = medio + 1;
        } else {
            derecha = medio - 1;
        }
    }

    archivo.close();
    return -1; // Elemento no encontrado
}

int main() {
    string nombreArchivo = "datos_ordenados.bin";
    int clave = 25;

    long resultado = busquedaBinariaArchivo(nombreArchivo, clave);
    if (resultado == -1) {
        cout << "Elemento no encontrado en el archivo." << endl;
    } else {
        cout << "Elemento encontrado en la posición: " << resultado << endl;
    }

    return 0;
}
```

**Explicación** 📖:
- **Apertura del Archivo**: Se abre el archivo para ser leído en modo binario. 📂
- **Determinación del Tamaño del Archivo**: Se calcula el número total de elementos en el archivo para definir los límites de la búsqueda. 📏
- **Búsqueda Binaria**: Se divide repetidamente el rango de búsqueda hasta encontrar el elemento o determinar que no está presente. 🔍

**Complejidad** ⏱️:
- **Mejor caso**: O(1) - si el elemento se encuentra en el primer intento. 🚀
- **Promedio y peor caso**: O(log n) - debido a la división iterativa del conjunto de datos. 📊

**Uso Práctico** 🎓:
La Búsqueda Binaria Externa se utiliza en aplicaciones que necesitan acceder rápidamente a grandes cantidades de datos ordenados en almacenamiento secundario, como bases de datos o grandes archivos de registros. Este método es ideal para optimizar el número de accesos a disco, mejorando la eficiencia de la búsqueda. 📚

# 4. 4. Hashing Externo 🔐

El Hashing Externo es una técnica utilizada para gestionar grandes volúmenes de datos que se encuentran almacenados en dispositivos externos, como discos duros. Utiliza una función hash para distribuir los datos en diferentes bloques, conocidos como "buckets", almacenados externamente. Esto permite acceder a los datos de manera muy eficiente, minimizando el número de accesos al disco. 📊

**Ventajas** ✅:
- Alta eficiencia en el acceso a los datos, con una complejidad promedio de O(1). ⚡
- Buena distribución de datos, lo que reduce los conflictos de acceso y mejora el rendimiento. 📈

**Desventajas** ❌:
- Puede haber colisiones que necesiten ser gestionadas adecuadamente para evitar la pérdida de datos. ⚠️
- Requiere más espacio para almacenar los buckets y, en algunos casos, las listas de desbordamiento. 🗂️

**Código en C++** 💻:
```cpp
#include <iostream>
#include <fstream>
#include <vector>
using namespace std;

const int NUM_BUCKETS = 10;

// Función hash para calcular el índice del bucket
int funcionHash(int clave) {
    return clave % NUM_BUCKETS;
}

void insertarEnArchivo(const string& nombreArchivo, int clave) {
    fstream archivo(nombreArchivo, ios::in | ios::out | ios::binary);
    if (!archivo.is_open()) {
        // Si el archivo no existe, crear uno nuevo
        archivo.open(nombreArchivo, ios::out | ios::binary);
        archivo.close();
        archivo.open(nombreArchivo, ios::in | ios::out | ios::binary);
    }

    int bucket = funcionHash(clave);
    archivo.seekp(bucket * sizeof(int), ios::beg);
    archivo.write(reinterpret_cast<char*>(&clave), sizeof(clave));
    archivo.close();
}

void buscarEnArchivo(const string& nombreArchivo, int clave) {
    fstream archivo(nombreArchivo, ios::in | ios::binary);
    if (!archivo.is_open()) {
        cout << "No se pudo abrir el archivo." << endl;
        return;
    }

    int bucket = funcionHash(clave);
    archivo.seekg(bucket * sizeof(int), ios::beg);
    int dato;
    archivo.read(reinterpret_cast<char*>(&dato), sizeof(dato));

    if (dato == clave) {
        cout << "Elemento " << clave << " encontrado en el archivo." << endl;
    } else {
        cout << "Elemento " << clave << " no encontrado en el archivo." << endl;
    }

    archivo.close();
}

int main() {
    string nombreArchivo = "hashing_externo.bin";
    insertarEnArchivo(nombreArchivo, 25);
    insertarEnArchivo(nombreArchivo, 15);
    insertarEnArchivo(nombreArchivo, 35);

    buscarEnArchivo(nombreArchivo, 25);
    buscarEnArchivo(nombreArchivo, 40);

    return 0;
}
```

**Explicación** 📖:
- **Función Hash**: Se utiliza una función hash simple (`clave % NUM_BUCKETS`) para determinar el bucket donde se almacenará la clave. 🔢
- **Inserción en el Archivo**: Cada clave se inserta en el bucket correspondiente en el archivo. Si el archivo no existe, se crea primero. 📂
- **Búsqueda en el Archivo**: Se calcula el bucket de la clave y luego se verifica si la clave está almacenada allí. 🔍

**Complejidad** ⏱️:
- **Mejor caso**: O(1) - si no hay colisiones y la función hash distribuye bien los elementos. 🚀
- **Peor caso**: O(n) - si hay muchas colisiones y se necesita recorrer una lista de desbordamiento. ❌

**Uso Práctico** 🎓:
El Hashing Externo se utiliza en sistemas de archivos, bases de datos y aplicaciones donde se necesita acceso rápido a registros almacenados externamente. Es ideal para manejar grandes volúmenes de datos que no caben completamente en memoria principal y donde se requiere un acceso rápido y eficiente. 📚













