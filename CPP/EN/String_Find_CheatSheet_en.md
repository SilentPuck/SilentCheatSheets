# 🕶 Cheat Sheet: Finding Characters in a String (std::string::find)

## 📌 Basics
The .find method of std::string searches for a character or substring.

- If found → returns position (index).  
- If not found → returns std::string::npos.

---

## 🔹 Check if a character exists in a string

```cpp
std::string vowels = "aeiou";
char ch = 'e';

if (vowels.find(ch) != std::string::npos) {
    // character 'e' found in vowels
}
```

---

## 🔹 Using in a loop (example with vowels/consonants)

```cpp
std::string vowels = "aeiou";
std::string consonants = "bcdfghjklmnpqrstvwxyz";
std::string word = "SilentPuck";

int vowelCount = 0;
int consonantCount = 0;

for (char ch : word) {
    if (!isalpha(ch)) continue;       // skip non-letters
    ch = tolower(ch);                 // convert to lowercase

    if (vowels.find(ch) != std::string::npos)
        vowelCount++;
    else if (consonants.find(ch) != std::string::npos)
        consonantCount++;
}
```

---

## 🔹 Notes
- Comparison is case-sensitive: 'A' and 'a' are different.  
  That’s why tolower() or toupper() is often used before find.  
- npos = special value "not found".  

---

## 🎯 Key points
- `str.find(ch) != std::string::npos` → character found.  
- `str.find(ch) == std::string::npos` → character not found.  

---

With silence and precision. — SilentPuck 🕶️
