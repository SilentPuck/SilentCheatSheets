# 🕶 CheatSheet: Why do <cctype> functions return int?

## 📖 History
Functions like `tolower`, `toupper`, `isalpha`, `isspace`, and others came from the **C language**.

In C, `char` was not always enough for every case, so the return type **int** was chosen.

---

## 📌 Reason 1. EOF support
- In C, file reading is done with `fgetc`:
  ```c
  int ch = fgetc(file);
  ```
- Why `int`?
  - `fgetc` returns **either a character** (0–255),  
  - or the special value **EOF = -1** when the file ends.

If `tolower` returned `char`, then `EOF` (=-1) would not fit into `unsigned char`, and we would lose the ability to detect end of file.

---

## 📌 Reason 2. Compatibility with C
The C++ standard kept C behavior for compatibility.

Therefore, all `<cctype>` functions:
- take `int` (not `char`),
- return `int`.

---

## 📌 What this means in C++
- For letters and digits, the result can be **safely cast to char**:
  ```cpp
  ch = static_cast<char>(tolower(ch));
  ```
- For arbitrary data (e.g., file reading) it’s useful to check `!= EOF`:
  ```c
  int ch;
  while ((ch = fgetc(file)) != EOF) {
      ch = tolower(ch);
      putchar(ch);
  }
  ```

---

## 🎯 Key points
- `tolower` and similar functions return `int` because they must be able to return `EOF`.
- In string tasks with letters → cast to `char` is safe.
- In file tasks → use `int` and check `!= EOF`.

---

With silence and precision. — SilentPuck 🕶️
