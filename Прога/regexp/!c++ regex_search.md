берем текст и помещаем его в файл source.txt, чтобы не париться с экранированием символов
```text
<a href="https://www.yandex.ru" asdsdas="ss"> gasdfdsj;faljfljdafj;slfjdsfsdfdsf 
fsdfdsfdsafdf<href="https://www.yandex.ru/aaa.html">asdfdsfasdfasdfasdfdsfaf
asdfdsafdasfasdffasdfdsfdsafdasfdsfdsfdasfdasfdasfdasfdasfdsafdasfasdfasdsf
asdfsdafdsfdasfdsaf.msd.amfdasnf,dm.asnf.,mnds,f.mnsda.,fnsda.,fnsdfdasfadsfdsfaf
```
теперь пишем простой код:
```c++
#include <iostream>
#include <fstream>
#include <sstream>
#include <regex>
using namespace std;
static string readFile(const string& fileName) {
	ifstream f(fileName);
	stringstream ss;
	ss << f.rdbuf();
	return ss.str();
}
int main() {
	string src = readFile("source.txt");
	regex reg ("href\\s?=\\s?\"(https?:\\/\\/[a-z\\.\\/]+)?\"");
	smatch result;
	if (regex_search(src, result, reg)) {
		cout << result[0] << "-----" << result[1] << endl;
	}
	else 
		cout << "Not found";
	return 0;
}
```
Получаем такой вывод:
```text
href="https://www.yandex.ru"-----https://www.yandex.ru
```
[0]- то что сматчилось  -----------[1] то, что в скобках

Но нам-то нужны все совпадения !

пишем:
```c++
include <iostream>
#include <fstream>
#include<sstream>
#include <regex>
using namespace std;
static string readFile(const string& fileName) {
	ifstream f(fileName);
	stringstream ss;
	ss << f.rdbuf();
	return ss.str();
}
int main() {
	string src = readFile("source.txt");
	regex reg ("href\\s?=\\s?\"(https?:\\/\\/[a-z\\.\\/]+)?\"");
	smatch result;
	while (regex_search(src, result, reg)) {
		cout << result[1] << endl;
		//внутри while бесконечно будет вестись поиск одного и того же фрагмента.
		// поэтому после поиска возьмем оставшийся после поиска кусок
		src = result.suffix();
	}
	return 0;
}
```
после этого мы получим все совпадения.
Но мы портим исходную строку и постоянно копируем содержимое строки.
поэтому попробуем на итераторах.
