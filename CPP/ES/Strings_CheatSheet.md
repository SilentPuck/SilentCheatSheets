# 🕶 Hoja de trucos: std::string en C++

La clase `std::string` de `<string>` simplifica el trabajo con cadenas.

---

## 🔹 1. Creación e ingreso

```cpp
#include <iostream>
#include <string>

std::string s1 = "Hello";
std::string s2;
std::cin >> s2; // entrada sin espacios
```

---

## 🔹 2. Longitud de la cadena

```cpp
s1.length(); // 5
s1.size();   // 5 (igual)
```

---

## 🔹 3. Indexación y acceso

```cpp
char c = s1[0];    // 'H'
char c2 = s1.at(1); // 'e'
```

---

## 🔹 4. Concatenación y adición

```cpp
std::string s3 = s1 + " World"; // "Hello World"
s1 += "!";                      // "Hello!"
```

---

## 🔹 5. Subcadenas y búsqueda

```cpp
std::string text = "abcdef";
std::string sub = text.substr(2, 3); // "cde"

size_t pos = text.find("cd"); // 2
if (pos != std::string::npos) {
    // encontrado
}
```

---

## 🔹 6. Conversiones

```cpp
std::string num = "123";
int x = std::stoi(num); // 123

int y = 42;
std::string str = std::to_string(y); // "42"
```

---

With silence and precision. — SilentPuck 🕶️
