При передачи regexp в c++ ОБЯЗАТЕЛЬНО экранировать backslash !!!

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
	cout << "Date";
	if (is_correct)
		cout << " is correct";
	else
		cout << " is incorrect";
	return 0;
```
