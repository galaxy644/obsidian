[[Ссылки обуч]]

[[Однострочники с++]]

[[chrono]]

[[Функции]]

[[Классы]]

[[Сортировки]]

[[Массивы]]

[[Системы счисления]]

[[Контейнеры std--]]

  

  

[[IO]]

[[Строки c++]]

[[Regexp c++]]

[[Генерация случайных Чисел]]

[[Дин.память]]

[[static_cast]]

[[std--memmove();]]

[[del item from arr]]

[[random]]

[[Битовые операции]]

[[Встроенные быстрые макросы GCC]]

[[Смена знака числа через дополненный код]]

[[Exceptions]]

  

- Создать Alias типа можно так==:==

==using Synonims map<string,set<string>> // Создали псевдоним.==

==Теперь пишем==

==void printSynonims(Synonims & syn){ }==

  

  

- ==В вот так можно не проверять пустую переменную====:==

`getline(cin, s);`  
  
`if (!s.empty() && s[0] == 'z'`

- Так можно вывести bool переменные словами.

`cout << boolalpha << true << endl` `_// Выведет true_`

- Високосный год

`bool year_is_leap = year % 4 == 0 && (year % 100 != 0 || year % 400 == 0);`

- Как конвертировать вектор в set

`std::vectorstd::string v; std::setstd::string s(v.begin(), v.end());`

- Range based for для set

`for(const auto& [key, val] : my_dict`)

- Функция, которая увеличивает значение аргумента в 2 раза

`auto f = [](int&a){a+=a;};`

- Формула приведения отрицательного остатка от деления к положительному

`a % b = (a % b + b) % b`

  

  

[[Const]]

[[Целочисленные типы]]

[[Кортежи]]

[[Time]]

[[std--exchange()]]

[[std--midpoint()]]

[[std--copy]]

[[std--bitset]]

[[SQLITE]]

[[init объектов через {}]]

[[pow без рекурсии]]

[[Ссылки как результат функции]]

[[min с var args]]

[[Add диап. в контейнер]]

[[exception]]

[[Локализация]]