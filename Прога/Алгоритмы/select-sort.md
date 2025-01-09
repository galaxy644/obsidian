Находим максимум в массиве и ставим его в конец массива.

Повторяем операцию на меньшем массиве. сложность

$$n*(n-1)/2 = O(N^2)$$

```C++
\#include <iostream>
using namespace std;
template<typename T>
void sortSelect(T array[], size_t sz) {
for (auto i = 0; i < sz; i++) {
			size_t index = 0;
			for (auto j = 0; j < sz - i; j++) {
					if (array[index] < array[j])
							index = j;
			}
swap(array[sz - 1 - i], array[index]);
}
```

```C++
}
int main()
{
char str[] = "94723941074";
sortSelect(str, 11);
cout << str << endl;
return 0;
}
```