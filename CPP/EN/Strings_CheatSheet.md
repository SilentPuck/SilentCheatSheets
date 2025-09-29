# 🕶 CheatSheet: std::string in C++

The `std::string` class from `<string>` simplifies working with strings.

---

## 🔹 1. Creation and input

```cpp
#include <iostream>
#include <string>

std::string s1 = "Hello";
std::string s2;
std::cin >> s2; // input without spaces
```

---

## 🔹 2. String length

```cpp
s1.length(); // 5
s1.size();   // 5 (same)
```

---

## 🔹 3. Indexing and access

```cpp
char c = s1[0];    // 'H'
char c2 = s1.at(1); // 'e'
```

---

## 🔹 4. Concatenation and appending

```cpp
std::string s3 = s1 + " World"; // "Hello World"
s1 += "!";                      // "Hello!"
```

---

## 🔹 5. Substrings and search

```cpp
std::string text = "abcdef";
std::string sub = text.substr(2, 3); // "cde"

size_t pos = text.find("cd"); // 2
if (pos != std::string::npos) {
    // found
}
```

---

## 🔹 6. Conversions

```cpp
std::string num = "123";
int x = std::stoi(num); // 123

int y = 42;
std::string str = std::to_string(y); // "42"
```

---

With silence and precision. — SilentPuck 🕶️
