```C++
\#include <iostream>
\#include <vector>
\#include <iterator>
\#include <algorithm>
using namespace std;
int main () {
vector<string> vec={"aaa","bbb","ccc"};
vector<string> dst_vec;
//Выводим все элементы вектора
copy(vec.begin(), vec.end(), ostream_iterator<string>(cout," "));
cout<<endl;
//Копируем все элементы во второй вектор;
copy(vec.begin(), vec.end(), inserter(dst_vec,dst_vec.begin()));
// Еще раз копируем все элементы в конец второго вектора;
copy(vec.begin(), vec.end(), dst_vec.begin()+1);
// А вот так мы не вставляем, а перезаписываем элементы вектора dst_vec;
copy(vec.begin(), vec.end(), back_inserter(dst_vec));
//Выводим все элементы второго вектора
copy(dst_vec.begin(), dst_vec.end(), ostream_iterator<string>(cout," "));
```

```C++
copy_if(dst_vec.begin(), dst_vec.end(), ostream_iterator<string>(cout," "),[](string s) {
return s[0]=='a';
});
// А здесь вывели все элекменты вектора, начинающиеся с буквы "a".
cout<<endl;
// Удалим все элементы, которые начинаются с "a"
dst_vec.erase(std::remove_if(dst_vec.begin(), dst_vec.end(),[](string s) {
return s[0]=='a';
}));
//И еще раз выведем вектор (уже отфильтрованный.
copy(dst_vec.begin(), dst_vec.end(), ostream_iterator<string>(cout," "));
}
```