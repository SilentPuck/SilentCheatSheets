# 🕶 CheatSheet: Characters ↔ Numbers in C++

## 🔹 1. Character = Number (ASCII/UTF-8)
Each `char` stores the numeric code of the character.

Examples (ASCII):
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

## 🔹 2. Digits
Convert a digit character to a number:
```cpp
char ch = '7';
int x = ch - '0'; // x = 7
```

Back (number to char):
```cpp
int y = 5;
char c = '0' + y; // c = '5'
```

---

## 🔹 3. Letters (Latin)
Convert a letter to an index:
```cpp
char ch = 'c';
int index = ch - 'a'; // index = 2 (0 = 'a', 1 = 'b', ...)
```

Back (index to letter):
```cpp
int idx = 2;
char letter = 'a' + idx; // letter = 'c'
```

Same for uppercase:
```cpp
char ch = 'C';
int index = ch - 'A'; // index = 2
char letter = 'A' + index; // 'C'
```

---

## 📌 Remember forever
- '0' → base for digits
- 'a' → base for lowercase letters
- 'A' → base for uppercase letters

---

## 🎯 Usage
- Count digits: `digits[ch - '0']++`
- Count letters: `freq[ch - 'a']++`
- Restore character from number: `'0' + i`, `'a' + i`, `'A' + i`

---

With silence and precision. — SilentPuck 🕶️
