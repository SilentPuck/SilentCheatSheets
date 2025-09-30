# Шпаргалка: поиск максимума в массиве и контейнерах C++

## 1. Поиск максимума вручную (C-style массив)
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

- Начинаем с `arr[0]` как максимума.  
- Перебираем все элементы.  
- При нахождении большего обновляем значение и индекс.

---

## 2. Современный вариант: `std::max_element` (C++11+)
```cpp
#include <algorithm>
#include <iostream>

int arr[10] = {7,8,4,3,4,2,1,0,9,6};

auto it = std::max_element(std::begin(arr), std::end(arr));

int maxValue = *it;                                 // значение
int index = std::distance(std::begin(arr), it);     // индекс

std::cout << "Max: " << maxValue << "\nIndex: " << index << std::endl;
```

- `std::begin(arr)` и `std::end(arr)` дают диапазон.  
- `std::max_element` возвращает итератор (по сути, указатель).  
- `*it` — разыменование, получаем значение.  
- `std::distance` — превращает итератор в индекс.

---

## 3. Пример с `std::vector`
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

- Удобнее и безопаснее, чем обычный массив.  
- `v.begin()` и `v.end()` работают так же, как `std::begin/ end` для массивов.

---

## 4. Когда использовать
- Для обучения и простых случаев — цикл `for`.  
- Для современного кода (особенно с STL-контейнерами) — `std::max_element`.  
- Для более сложных задач можно комбинировать с другими алгоритмами STL.

---

With silence and precision. — SilentPuck 🕶️
