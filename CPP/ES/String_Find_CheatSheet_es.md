# 🕶 Hoja de trucos: búsqueda de caracteres en una cadena (std::string::find)

## 📌 Conceptos básicos
El método .find de std::string busca un carácter o subcadena.

- Si se encuentra → devuelve la posición (índice).  
- Si no se encuentra → devuelve std::string::npos.

---

## 🔹 Comprobar si un carácter existe en la cadena

```cpp
std::string vowels = "aeiou";
char ch = 'e';

if (vowels.find(ch) != std::string::npos) {
    // el carácter 'e' se encontró en vowels
}
```

---

## 🔹 Uso en un bucle (ejemplo con vocales/consonantes)

```cpp
std::string vowels = "aeiou";
std::string consonants = "bcdfghjklmnpqrstvwxyz";
std::string word = "SilentPuck";

int vowelCount = 0;
int consonantCount = 0;

for (char ch : word) {
    if (!isalpha(ch)) continue;       // saltar no letras
    ch = tolower(ch);                 // convertir a minúscula

    if (vowels.find(ch) != std::string::npos)
        vowelCount++;
    else if (consonants.find(ch) != std::string::npos)
        consonantCount++;
}
```

---

## 🔹 Notas
- La comparación distingue mayúsculas/minúsculas: 'A' y 'a' son diferentes.  
  Por eso se usa tolower() o toupper() antes de find.  
- npos = valor especial "no encontrado".  

---

## 🎯 Claves
- `str.find(ch) != std::string::npos` → carácter encontrado.  
- `str.find(ch) == std::string::npos` → carácter no encontrado.  

---

With silence and precision. — SilentPuck 🕶️
