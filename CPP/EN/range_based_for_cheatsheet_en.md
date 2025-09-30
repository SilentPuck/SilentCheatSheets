# Cheat Sheet: Range-based for loop in C++

## 1. Syntax
```cpp
for (auto x : container) {
    // use x
}
```
- `x` takes the values of all elements in the container (array, vector, string).  
- Works since C++11.  

---

## 2. How it works
Example:
```cpp
std::vector<int> v = {10, 20, 30};
for (auto x : v)
    std::cout << x << " ";
```
Output:
```
10 20 30
```

---

## 3. Using references
By default, `x` is a **copy of the element**.  
If you need to modify elements:
```cpp
for (auto& x : v)
    x *= 2; // doubles all elements
```
If you only want to read without copying (e.g. strings):
```cpp
for (const auto& x : v)
    std::cout << x << " ";
```

---

## 4. Examples with different containers

### std::array
```cpp
std::array<int, 5> arr = {1,2,3,4,5};
for (auto x : arr)
    std::cout << x << " ";
```

### std::vector
```cpp
std::vector<int> v = {1,2,3,4,5};
for (auto& x : v)   // reference → modify elements
    x += 10;
```

### std::string
```cpp
std::string s = "Hello";
for (auto ch : s)
    std::cout << ch << " ";
```

---

## 5. When to use
- For simple iteration over all elements.  
- For output or processing without index.  
- When the type is complex (`std::pair`, `std::tuple`) → convenient with `auto`.  

## 6. When classic for is better
- When you need the index (`i = 0..size-1`).  
- When modifying container size during iteration (`push_back`, `erase`).  

---

With silence and precision. — SilentPuck 🕶️
