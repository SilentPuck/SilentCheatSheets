# Chuleta: std::array en C++

## 1. Qué es
- Un contenedor de la STL con tamaño fijo (como un arreglo C).  
- Conoce su tamaño (`.size()`) y funciona con algoritmos de la STL.  
- Más seguro y cómodo que un arreglo en C.  
- Se incluye con `<array>`.

---

## 2. Declaración
```cpp
#include <array>

std::array<int, 5> arr = {1, 2, 3, 4, 5};
std::array<int, 10> arr2 = {}; // все нули
```

---

## 3. Acceso a elementos
```cpp
arr[0];        // como un arreglo normal (sin verificación de límites)
arr.at(0);     // con verificación de límites (lanza std::out_of_range)
arr.front();   // primer elemento
arr.back();    // último elemento
```

---

## 4. Métodos
```cpp
arr.size();    // número de elementos
arr.fill(7);   // rellenar todos los elementos con un valor
```

---

## 5. Uso con algoritmos de la STL
```cpp
#include <algorithm>

auto it = std::max_element(arr.begin(), arr.end());
int maxValue = *it;

std::reverse(arr.begin(), arr.end()); // invertir
std::sort(arr.begin(), arr.end());    // ordenación
```

---

## 6. Diferencias con un arreglo C
- Los arreglos C no tienen `.size()` ni métodos.  
- `std::array` tiene métodos útiles y soporte de la STL.  
- Tamaño fijo en compilación; más seguro de usar.  

---

## 7. Cuándo usar
- Cuando el tamaño es fijo y conocido en compilación.  
- Cuando necesitas un arreglo 'como C' pero con seguridad y comodidad de la STL.  
- Si necesitas tamaño dinámico → usa `std::vector`.

---

Con silencio y precisión. — SilentPuck 🕶️
