# Hoja de trucos: bucle for basado en rango en C++

## 1. Sintaxis
```cpp
for (auto x : container) {
    // usar x
}
```
- `x` toma los valores de todos los elementos del contenedor (array, vector, string).  
- Funciona desde C++11.  

---

## 2. Cómo funciona
Ejemplo:
```cpp
std::vector<int> v = {10, 20, 30};
for (auto x : v)
    std::cout << x << " ";
```
Salida:
```
10 20 30
```

---

## 3. Uso de referencias
Por defecto, `x` es una **copia del elemento**.  
Si necesitas modificar los elementos:
```cpp
for (auto& x : v)
    x *= 2; // duplica todos los elementos
```
Si solo quieres leer sin copiar (por ejemplo, strings):
```cpp
for (const auto& x : v)
    std::cout << x << " ";
```

---

## 4. Ejemplos con diferentes contenedores

### std::array
```cpp
std::array<int, 5> arr = {1,2,3,4,5};
for (auto x : arr)
    std::cout << x << " ";
```

### std::vector
```cpp
std::vector<int> v = {1,2,3,4,5};
for (auto& x : v)   // referencia → modifica elementos
    x += 10;
```

### std::string
```cpp
std::string s = "Hello";
for (auto ch : s)
    std::cout << ch << " ";
```

---

## 5. Cuándo usarlo
- Para recorrer fácilmente todos los elementos.  
- Para imprimir o procesar sin índice.  
- Cuando el tipo es complejo (`std::pair`, `std::tuple`) → práctico con `auto`.  

## 6. Cuándo es mejor el for clásico
- Cuando necesitas el índice (`i = 0..size-1`).  
- Cuando cambias el tamaño del contenedor durante la iteración (`push_back`, `erase`).  

---

With silence and precision. — SilentPuck 🕶️
