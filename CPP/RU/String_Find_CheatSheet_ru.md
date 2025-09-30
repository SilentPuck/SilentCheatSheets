# 🕶 Шпаргалка: поиск символа в строке (std::string::find)

## 📌 Основное
Метод .find у std::string ищет символ или подстроку.

- Если найдено → возвращает позицию (индекс).
- Если не найдено → возвращает std::string::npos.

---

## 🔹 Проверка, есть ли символ в строке

```cpp
std::string vowels = "aeiou";
char ch = 'e';

if (vowels.find(ch) != std::string::npos) {
    // символ 'e' найден в строке vowels
}
```

---

## 🔹 Использование в цикле (пример с гласными/согласными)

```cpp
std::string vowels = "aeiou";
std::string consonants = "bcdfghjklmnpqrstvwxyz";
std::string word = "SilentPuck";

int vowelCount = 0;
int consonantCount = 0;

for (char ch : word) {
    if (!isalpha(ch)) continue;       // пропускаем всё кроме букв
    ch = tolower(ch);                 // приводим к нижнему регистру

    if (vowels.find(ch) != std::string::npos)
        vowelCount++;
    else if (consonants.find(ch) != std::string::npos)
        consonantCount++;
}
```

---

## 🔹 Особенности
- Сравнение чувствительно к регистру: 'A' и 'a' разные.  
  Поэтому часто используют tolower() или toupper() перед find.  
- npos = специальное значение «не найдено».  

---

## 🎯 Главное
- `str.find(ch) != std::string::npos` → символ найден.  
- `str.find(ch) == std::string::npos` → символа нет.  

---

With silence and precision. — SilentPuck 🕶️
