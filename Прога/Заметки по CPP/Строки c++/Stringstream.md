\#include <sstream>  
string str="abacaba"  
std::stringstream ss(str);  
string str1=ss.str();  

Методы работы с потоками:

stream.ignore(n) - пропустить n символов из потока

stream.peek() - смотрит какой символ в потоке следующий

```C++
vector<int> parseInts(string str) {
int temp;
stringstream ss(str);
vector<int> result;
while (ss>>temp) {
result.push_back(temp);
ss.ignore(1);
}
return result;
}
```