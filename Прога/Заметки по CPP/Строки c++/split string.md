```C++
/*
ниже приводятся две версии функции разбиения строк на лексемы.
Первая принимает единственный символ разделителя. Она разбивает
входную строку с использованием строкового потока, инициализированного
ее содержимым, применяя std::getline() для чтения фрагментов, пока не
встретится следующий разделитель или признак конца  строки.
Вторая принимает список возможных разделителей в виде std::string.
Она использует std:string::find_first_of() для поиска первого из символов-разделителей
и переходит к первому символу за ним. Операция повторяется в цикле, пока не будет
обработана вся входная строка. Извлеченные подстроки добавляются в вектор, играющий роль результата:
*/
\#include <vector>
\#include <iostream>
\#include <cassert>
\#include <string>
\#include <sstream>
```

```C++
template <class Elem>
using tstring = std::basic_string<Elem, std::char_traits<Elem>,
std::allocator<Elem>>;
template <class Elem>
using tstringstream = std::basic_stringstream<
Elem, std::char_traits<Elem>, std::allocator<Elem>>;
template<typename Elem>
inline std::vector<tstring<Elem>> split(tstring<Elem> text,
Elem const delimiter)
{
auto sstr = tstringstream<Elem>{ text };
auto tokens = std::vector<tstring<Elem>>{};
auto token = tstring<Elem>{};
while (std::getline(sstr, token, delimiter))
{
if (!token.empty()) tokens.push_back(token);
}
return tokens;
}
template<typename Elem>
inline std::vector<tstring<Elem>> split(tstring<Elem> text,
tstring<Elem> const& delimiters)
{
auto tokens = std::vector<tstring<Elem>>{};
size_t pos, prev_pos = 0;
while ((pos = text.find_first_of(delimiters, prev_pos)) !=
std::string::npos)
{
if (pos > prev_pos)
tokens.push_back(text.substr(prev_pos, pos - prev_pos));
prev_pos = pos + 1;
}
if (prev_pos < text.length())
tokens.push_back(text.substr(prev_pos, std::string::npos));
return tokens;
}
//Следующий листинг демонстрирует два примера разбиения строк по одному или по нескольким разделителям:
int main()
{
using namespace std::string_literals;
std::vectorstd::string expected{ "this", "is", "a", "sample" };
assert(expected == split("this is a sample"s, ' '));
assert(expected == split("this,is a.sample!!"s, ",.! "s));
}
```