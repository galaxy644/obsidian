Программа ищет самое длинное слово в строке

```C++
\#include <iostream>
\#include <string>
using namespace std;
int main() {
    string ms = "", s;
    while(cin >> s) {
        if (ms.length() < s.length())
            ms = s;
    }
    cout << ms;
    return 0;
}
```