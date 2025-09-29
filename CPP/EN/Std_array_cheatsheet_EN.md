# Cheatsheet: std::array in C++

## 1. What it is
- An STL container with a fixed size (like a C-style array).  
- Knows its size (`.size()`) and works with STL algorithms.  
- Safer and more convenient than a C array.  
- Include via `<array>`.

---

## 2. Declaration
```cpp
#include <array>

std::array<int, 5> arr = {1, 2, 3, 4, 5};
std::array<int, 10> arr2 = {}; // все нули
```

---

## 3. Element access
```cpp
arr[0];        // like a raw array (no bounds check)
arr.at(0);     // bounds-checked (throws std::out_of_range)
arr.front();   // first element
arr.back();    // last element
```

---

## 4. Methods
```cpp
arr.size();    // number of elements
arr.fill(7);   // fill all elements with a value
```

---

## 5. Using with STL algorithms
```cpp
#include <algorithm>

auto it = std::max_element(arr.begin(), arr.end());
int maxValue = *it;

std::reverse(arr.begin(), arr.end()); // reverse
std::sort(arr.begin(), arr.end());    // sort
```

---

## 6. Differences from a C array
- C arrays have no `.size()` and no methods.  
- `std::array` has convenient methods and STL support.  
- Fixed size at compile time; safer to use.  

---

## 7. When to use
- When the size is fixed and known at compile time.  
- When you want a 'C-like' array with STL safety and convenience.  
- If you need a dynamic size → use `std::vector`.

---

With silence and precision. — SilentPuck 🕶️
