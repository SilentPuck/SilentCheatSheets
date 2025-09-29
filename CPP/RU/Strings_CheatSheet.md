# 🕶 Шпаргалка: std::string в C++

Класс `std::string` из `<string>` облегчает работу со строками.

---

## 🔹 1. Создание и ввод

```cpp
#include <iostream>
#include <string>

std::string s1 = "Hello";
std::string s2;
std::cin >> s2; // ввод без пробелов
```

---

## 🔹 2. Длина строки

```cpp
s1.length(); // 5
s1.size();   // 5 (то же самое)
```

---

## 🔹 3. Индексация и доступ

```cpp
char c = s1[0];    // 'H'
char c2 = s1.at(1); // 'e'
```

---

## 🔹 4. Сложение и добавление

```cpp
std::string s3 = s1 + " World"; // "Hello World"
s1 += "!";                      // "Hello!"
```

---

## 🔹 5. Подстроки и поиск

```cpp
std::string text = "abcdef";
std::string sub = text.substr(2, 3); // "cde"

size_t pos = text.find("cd"); // 2
if (pos != std::string::npos) {
    // найдено
}
```

---

## 🔹 6. Преобразования

```cpp
std::string num = "123";
int x = std::stoi(num); // 123

int y = 42;
std::string str = std::to_string(y); // "42"
```

---

With silence and precision. — SilentPuck 🕶️
