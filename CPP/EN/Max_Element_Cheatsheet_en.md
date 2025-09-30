# Cheat Sheet: Finding the Maximum in Arrays and Containers in C++

## 1. Manual search (C-style array)
```cpp
constexpr int SIZE = 10;
int arr[SIZE] = {7,8,4,3,4,2,1,0,9,6};

int max = arr[0];
int index = 0;

for (int i = 1; i < SIZE; ++i) {
    if (arr[i] > max) {
        max = arr[i];
        index = i;
    }
}

std::cout << "Max: " << max << "\nIndex: " << index << std::endl;
```

- Start with `arr[0]` as the maximum.  
- Iterate through all elements.  
- Update value and index when a larger one is found.

---

## 2. Modern way: `std::max_element` (C++11+)
```cpp
#include <algorithm>
#include <iostream>

int arr[10] = {7,8,4,3,4,2,1,0,9,6};

auto it = std::max_element(std::begin(arr), std::end(arr));

int maxValue = *it;                                 // value
int index = std::distance(std::begin(arr), it);     // index

std::cout << "Max: " << maxValue << "\nIndex: " << index << std::endl;
```

- `std::begin(arr)` and `std::end(arr)` define the range.  
- `std::max_element` returns an iterator (basically, a pointer).  
- `*it` dereferences to get the value.  
- `std::distance` converts the iterator to an index.

---

## 3. Example with `std::vector`
```cpp
#include <vector>
#include <algorithm>
#include <iostream>

std::vector<int> v = {7,8,4,3,4,2,1,0,9,6};

auto it = std::max_element(v.begin(), v.end());

int maxValue = *it;
int index = std::distance(v.begin(), it);

std::cout << "Max: " << maxValue << "\nIndex: " << index << std::endl;
```

- More convenient and safer than a raw array.  
- `v.begin()` and `v.end()` work the same as `std::begin/ end` for arrays.

---

## 4. When to use
- For learning and simple cases → manual `for` loop.  
- For modern code (especially with STL containers) → `std::max_element`.  
- For more complex tasks, combine with other STL algorithms.

---

With silence and precision. — SilentPuck 🕶️
