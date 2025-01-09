```C++
\#include<iostream>
\#include <vector>
\#include <list>
\#include <array>
\#include<cassert>
\#include<iomanip>
\#include<sstream>
using namespace std;
/*
Чтобы функция могла обрабатывать коллекции разных видов, такие как std::array, std::vector, C-подобные массивы и др.,
мы должны написать шаблонную функцию. Далее приводятся две перегруженные версии; одна принимает контейнер и флаг,
определяющий регистр символов в выходной строке, а другая принимает пару итераторов (указывающих на первый и последний
элементы последовательности) и флаг регистра символов. Содержимое диапазона записывается в объект std::ostringstream
с использованием соответствующих манипуляторов ввода/вывода, таких как ширина, заполняющий символ и флаг регистра:
*/
template <typename Iter>
std::string bytes_to_hexstr(Iter begin, Iter end,
bool const uppercase = false)
{
std::ostringstream oss;
if (uppercase) oss.setf(std::ios_base::uppercase);
for (; begin != end; ++begin)
oss << std::hex << std::setw(2) << std::setfill('0')
<< static_cast<int>(begin);
return oss.str();
}
template <typename C>
std::string bytes_to_hexstr(C const& c, bool const uppercase = false)
{
return bytes_to_hexstr(std::cbegin(c), std::cend(c), uppercase);
}
int main()
{
std::vector<unsigned char> v{ 0xBA, 0xAD, 0xF0, 0x0D };
std::array<unsigned char, 6> a{ {1,2,3,4,5,6} };
unsigned char buf[5] = { 0x11, 0x22, 0x33, 0x44, 0x55 };
assert(bytes_to_hexstr(v, true) == "BAADF00D");
assert(bytes_to_hexstr(a, true) == "010203040506");
assert(bytes_to_hexstr(buf, true) == "1122334455");
assert(bytes_to_hexstr(v) == "baadf00d");
assert(bytes_to_hexstr(a) == "010203040506");
assert(bytes_to_hexstr(buf) == "1122334455");
}
/*
Напишите функцию, которая преобразует коллекцию 8-битных целых чисел
(массив или вектор) в строку с шестнадцатеричными их представлениями.
Функция должна поддерживать вывод символов в верхнем и в нижнем
регистрах. Вот несколько примеров входных данных и соответствующих им
строк на выходе:
Вход: { 0xBA, 0xAD, 0xF0, 0x0D }, выход: "BAADF00D" или "baadf00d"
Вход: { 1,2,3,4,5,6 }, выход: "010203040506"*/
```