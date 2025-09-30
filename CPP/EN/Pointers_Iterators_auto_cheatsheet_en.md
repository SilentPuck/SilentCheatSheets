# Cheat Sheet: Pointers, Iterators, and `auto` in C++

## 1. Pointers
- A pointer stores the **address** of a variable.
```cpp
int x = 42;
int* p = &x;       // p stores the address of x
std::cout << p;    // prints the address (e.g., 0x7ff...)
std::cout << *p;   // dereference, prints 42
```
- `*p` — dereference, access the value by address.  
- `&x` — "take address" operator.

---

## 2. Iterators
- An iterator is a "generalized pointer" for STL containers.  
- For arrays, iterators = raw pointers.  
- For `std::vector<int>`, iterator type is `std::vector<int>::iterator`.

Example:
```cpp
std::vector<int> v = {1,2,3};
auto it = v.begin();   // points to v[0]
std::cout << *it;      // dereference → 1
++it;                  // now points to v[1]
std::cout << *it;      // dereference → 2
```

---

## 3. `auto`
- `auto` tells the compiler: "deduce the type automatically".
```cpp
auto x = 5;        // int
auto y = 3.14;     // double
auto it = v.begin();  // std::vector<int>::iterator
```
- Simplifies code, especially with long types (`std::map<std::string, std::vector<int>>::iterator`).

---

## 4. Iterators and `*`
Example with `std::max_element`:
```cpp
int arr[5] = {7,3,9,1,5};
auto it = std::max_element(std::begin(arr), std::end(arr));

std::cout << *it;  // 9 → value
std::cout << it;   // address (like a pointer)
```
- `it` — is a pointer/iterator.  
- `*it` — value it points to.

---

## 5. Increment `++`
- Pointers and iterators support `++`.
```cpp
int arr[3] = {10, 20, 30};
int* p = arr;
std::cout << *p << std::endl;  // 10
++p;                           // move to next element
std::cout << *p << std::endl;  // 20
```
- Same works for iterators.

---

## 6. When to use `auto`
- When the type is long or obvious from context.  
- Example:
  ```cpp
  for (auto it = v.begin(); it != v.end(); ++it) {
      std::cout << *it << std::endl;
  }
  ```

---

With silence and precision. — SilentPuck 🕶️
