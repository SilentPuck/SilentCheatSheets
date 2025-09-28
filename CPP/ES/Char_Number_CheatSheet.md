# 🕶 Hoja de trucos: Caracteres ↔ Números en C++

## 🔹 1. Carácter = Número (ASCII/UTF-8)
Cada `char` almacena el código numérico del carácter.

Ejemplos (ASCII):
- '0' = 48
- '1' = 49
- '9' = 57
- 'A' = 65
- 'B' = 66
- 'Z' = 90
- 'a' = 97
- 'b' = 98
- 'z' = 122

---

## 🔹 2. Dígitos
Convertir un carácter dígito en número:
```cpp
char ch = '7';
int x = ch - '0'; // x = 7
```

Al revés (número a carácter):
```cpp
int y = 5;
char c = '0' + y; // c = '5'
```

---

## 🔹 3. Letras (latinas)
Convertir una letra en índice:
```cpp
char ch = 'c';
int index = ch - 'a'; // index = 2 (0 = 'a', 1 = 'b', ...)
```

Al revés (índice a letra):
```cpp
int idx = 2;
char letter = 'a' + idx; // letter = 'c'
```

Lo mismo para mayúsculas:
```cpp
char ch = 'C';
int index = ch - 'A'; // index = 2
char letter = 'A' + index; // 'C'
```

---

## 📌 Recordar siempre
- '0' → base para dígitos
- 'a' → base para letras minúsculas
- 'A' → base para letras mayúsculas

---

## 🎯 Uso
- Contar dígitos: `digits[ch - '0']++`
- Contar letras: `freq[ch - 'a']++`
- Recuperar carácter de número: `'0' + i`, `'a' + i`, `'A' + i`

---

With silence and precision. — SilentPuck 🕶️
