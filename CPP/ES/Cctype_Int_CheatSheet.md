# 🕶 Hoja de trucos: ¿Por qué las funciones de <cctype> devuelven int?

## 📖 Historia
Funciones como `tolower`, `toupper`, `isalpha`, `isspace` y otras vienen del **lenguaje C**.

En C, `char` no siempre era suficiente para todos los casos, por eso se eligió el tipo de retorno **int**.

---

## 📌 Razón 1. Soporte de EOF
- En C, la lectura de archivos se hace con `fgetc`:
  ```c
  int ch = fgetc(file);
  ```
- ¿Por qué `int`?
  - `fgetc` devuelve **un carácter** (0–255),  
  - o el valor especial **EOF = -1** cuando termina el archivo.

Si `tolower` devolviera `char`, entonces `EOF` (=-1) no cabría en un `unsigned char`, y perderíamos la posibilidad de detectar el fin de archivo.

---

## 📌 Razón 2. Compatibilidad con C
El estándar de C++ mantuvo el comportamiento de C por compatibilidad.

Por eso todas las funciones de `<cctype>`:
- aceptan `int` (no `char`),
- devuelven `int`.

---

## 📌 Qué significa en C++
- Para letras y dígitos, el resultado se puede **convertir de forma segura a char**:
  ```cpp
  ch = static_cast<char>(tolower(ch));
  ```
- Para datos arbitrarios (por ejemplo, lectura de archivos) es útil comprobar `!= EOF`:
  ```c
  int ch;
  while ((ch = fgetc(file)) != EOF) {
      ch = tolower(ch);
      putchar(ch);
  }
  ```

---

## 🎯 Lo esencial
- `tolower` y funciones similares devuelven `int` porque deben poder devolver `EOF`.
- En tareas de cadenas con letras → convertir a `char` es seguro.
- En tareas con archivos → usar `int` y comprobar `!= EOF`.

---

With silence and precision. — SilentPuck 🕶️
