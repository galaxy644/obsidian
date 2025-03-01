При передачи regexp в c++ ОБЯЗАТЕЛЬНО экранировать backslash !!!

```C++
#include <iostream>
#include <regex>
using namespace std;
int main() {
	string input;
	cin >> input;
	regex reg("^(3[0-1]||[12][0-9]||0?[1-9])\\.([1][0-2]||0?[1-9])\\.((?:19|20)\\d{2})");
	smatch result;
	
	bool is_correct= regex_match(input, result, reg);
	cout << "Date";
	if (is_correct)
		cout << " is correct";
	else
		cout << " is incorrect";
	return 0;
```

Теперь посмотрим что же находится в переменной result:
```c++
#include <iostream>
#include <regex>
using namespace std;
int main() {
	string input;
	cin >> input;
	regex reg("^(3[0-1]||[12][0-9]||0?[1-9])\\.([1][0-2]||0?[1-9])\\.((?:19|20)\\d{2})");
	smatch result;
	
	bool is_correct= regex_match(input, result, reg);
	if (is_correct)
		for (size_t i = 0; i < result.size(); i++)
		{
			cout<<" i = "<<i<<" contains \""<<result[i]<<"\"" << endl;
			
		}
	else
		cout <<"Date is incorrect";
	return 0;
}
```
А там находится вот это :
```text
 i = 0 contains "01.02.2021"
 i = 1 contains "01"
 i = 2 contains "02"
 i = 3 contains "2021"
```

Теперь разложим все по структуре Date
```C++
#include <iostream>
#include <regex>
using namespace std;
struct Date {
	int day;
	int month;
	int year;
};
int main() {
	string input;
	cin >> input;
	Date dt;
	regex reg("^(3[0-1]||[12][0-9]||0?[1-9])\\.([1][0-2]||0?[1-9])\\.((?:19|20)\\d{2})");
	smatch result;
	
	bool is_correct= regex_match(input, result, reg);
	if (is_correct) {
		dt.day = stoi(result[1]);
		dt.month = stoi(result[2]);
		dt.year = stoi(result[3]);
	}
	else
		cout <<"Date is incorrect";
	return 0;
}
```