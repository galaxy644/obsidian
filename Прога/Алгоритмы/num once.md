Алгоритм нахождения числа, встречающегося только 1 раз

```C++
\#include <iostream>
int main()
{
    int a, k = 0,n;
    std::cin>>n;
    for(;n;n--)
    {
        std::cin>>a
        k ^= a;
    }
    std::cout<<k;
    return 0;
}
```