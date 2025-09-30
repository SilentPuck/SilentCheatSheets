# 🕶 Hoja de trucos: operaciones básicas con cadenas y caracteres en C++

## 🔹 1. Caracteres (char)
- Cada carácter se almacena como un número (código ASCII).
- 'A' = 65, 'a' = 97, ' ' (espacio) = 32.
- Por lo tanto 'A' != 'a' (diferente mayúscula/minúscula).

👉 Para comparación sin distinguir mayúsculas, usa tolower o toupper.

---

## 🔹 2. Conversión de mayúsculas/minúsculas
- tolower(ch) → letra minúscula.
- toupper(ch) → letra mayúscula.

Ejemplo:
```cpp
if (tolower(word[i]) == tolower(word[j])) { ... }
```

---

## 🔹 3. Comprobaciones de caracteres (<cctype>)
- isalpha(ch) → letra.
- isdigit(ch) → dígito.
- isalnum(ch) → letra o dígito.
- isspace(ch) → espacio, tabulación, salto de línea.
- ispunct(ch) → signos de puntuación (! ? . , etc.).

---

## 🔹 4. Limpieza de cadenas
Mantener solo letras y dígitos (ignorar espacios y signos):

```cpp
std::string cleaned;
for (char ch : word)
    if (isalnum(ch)) cleaned += tolower(ch);
```

Ejemplo:
- Entrada: "Silent Puck, 2025!"
- Salida: "silentpuck2025"

---

## 🔹 5. Comparación de cadenas
- "abc" == "abc" → true  
- "abc" == "ABC" → false (diferente mayúscula/minúscula)

---

## 🔹 6. Inversión de cadenas
Método 1: construir una nueva cadena al revés.  
Método 2: intercambiar caracteres en el lugar.  
Método 3: STL → std::reverse(word.begin(), word.end());

---

## 🔹 7. Palíndromo
- Básico: comparar caracteres desde el inicio y el final.  
- Avanzado: convertir a minúsculas (tolower), eliminar espacios y signos (isalnum).

---

## 🔹 8. Contar caracteres
- Con bucle: if (ch == ' ') count++;  
- Con STL: int count = std::count(s.begin(), s.end(), ' ');

---

## 🎯 Claves
1. Recorrer la cadena en bucle.  
2. Comprobar caracteres (isspace, isalnum, tolower).  
3. Crear una versión "limpia" de la cadena.  
4. Invertir la cadena (reverse).  
5. Comprobar palíndromo (con/sin limpieza).

---

With silence and precision. — SilentPuck 🕶️
