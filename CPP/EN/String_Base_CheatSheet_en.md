# 🕶 Cheat Sheet: Basic String and Character Operations in C++

## 🔹 1. Characters (char)
- Each character is stored as a number (ASCII code).
- 'A' = 65, 'a' = 97, ' ' (space) = 32.
- Therefore 'A' != 'a' (different case).

👉 For case-insensitive comparison, use tolower or toupper.

---

## 🔹 2. Case conversion
- tolower(ch) → lowercase letter.
- toupper(ch) → uppercase letter.

Example:
```cpp
if (tolower(word[i]) == tolower(word[j])) { ... }
```

---

## 🔹 3. Character checks (<cctype>)
- isalpha(ch) → letter.
- isdigit(ch) → digit.
- isalnum(ch) → letter or digit.
- isspace(ch) → space, tab, newline.
- ispunct(ch) → punctuation marks (! ? . , etc.).

---

## 🔹 4. Cleaning strings
Keep only letters and digits (ignore spaces and punctuation):

```cpp
std::string cleaned;
for (char ch : word)
    if (isalnum(ch)) cleaned += tolower(ch);
```

Example:
- Input: "Silent Puck, 2025!"
- Output: "silentpuck2025"

---

## 🔹 5. String comparison
- "abc" == "abc" → true
- "abc" == "ABC" → false (different case)

---

## 🔹 6. String reversal
Method 1: build a new string backwards.  
Method 2: swap characters in place.  
Method 3: STL → std::reverse(word.begin(), word.end());

---

## 🔹 7. Palindrome
- Basic: compare characters from start and end.  
- Advanced: convert to lowercase (tolower), remove spaces and punctuation (isalnum).

---

## 🔹 8. Counting characters
- Using loop: if (ch == ' ') count++;  
- Using STL: int count = std::count(s.begin(), s.end(), ' ');

---

## 🎯 Key points
1. Iterate through string in a loop.  
2. Check characters (isspace, isalnum, tolower).  
3. Create a "cleaned" version of string.  
4. Reverse string (reverse).  
5. Check palindrome (with/without cleaning).

---

With silence and precision. — SilentPuck 🕶️
