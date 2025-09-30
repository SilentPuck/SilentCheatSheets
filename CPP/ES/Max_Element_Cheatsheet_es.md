# Hoja de trucos: encontrar el máximo en arrays y contenedores en C++

## 1. Búsqueda manual (array estilo C)
```cpp
constexpr int SIZE = 10;
int arr[SIZE] = {7,8,4,3,4,2,1,0,9,6};

int max = arr[0];
int index = 0;

for (int i = 1; i < SIZE; ++i) {
    if (arr[i] > max) {
        max = arr[i];
        index = i;
    }
}

std::cout << "Max: " << max << "\nIndex: " << index << std::endl;
```

- Empezamos con `arr[0]` como máximo.  
- Recorremos todos los elementos.  
- Actualizamos valor e índice al encontrar uno mayor.

---

## 2. Forma moderna: `std::max_element` (C++11+)
```cpp
#include <algorithm>
#include <iostream>

int arr[10] = {7,8,4,3,4,2,1,0,9,6};

auto it = std::max_element(std::begin(arr), std::end(arr));

int maxValue = *it;                                 // valor
int index = std::distance(std::begin(arr), it);     // índice

std::cout << "Max: " << maxValue << "\nIndex: " << index << std::endl;
```

- `std::begin(arr)` y `std::end(arr)` definen el rango.  
- `std::max_element` devuelve un iterador (básicamente, un puntero).  
- `*it` desreferencia y obtiene el valor.  
- `std::distance` convierte el iterador en índice.

---

## 3. Ejemplo con `std::vector`
```cpp
#include <vector>
#include <algorithm>
#include <iostream>

std::vector<int> v = {7,8,4,3,4,2,1,0,9,6};

auto it = std::max_element(v.begin(), v.end());

int maxValue = *it;
int index = std::distance(v.begin(), it);

std::cout << "Max: " << maxValue << "\nIndex: " << index << std::endl;
```

- Más cómodo y seguro que un array normal.  
- `v.begin()` y `v.end()` funcionan igual que `std::begin/ end` para arrays.

---

## 4. Cuándo usarlo
- Para aprendizaje y casos simples → bucle `for` manual.  
- Para código moderno (especialmente con contenedores STL) → `std::max_element`.  
- Para tareas más complejas, combínalo con otros algoritmos de STL.

---

With silence and precision. — SilentPuck 🕶️
