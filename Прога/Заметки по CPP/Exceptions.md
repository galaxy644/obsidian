```C++
\#include <iostream>
\#include <sstream>
\#include <exception>
\#include <iomanip>
using namespace std;
struct Date{
int year;
int month;
int day;
};
void EnsureNextSymbolAndSkip(stringstream &stream){
if(stream.peek()!='/'){
stringstream ss;
ss<<"expected /, but has: "<<char(stream.peek());
throw runtime_error(ss.str());
}
stream.ignore(1);
}
Date parse_date(const string &s){
stringstream stream (s);
Date result;
stream>>result.year;
EnsureNextSymbolAndSkip(stream);
stream>>result.month;
EnsureNextSymbolAndSkip(stream);
stream>>result.day;
return result;
}
int main()
{
try{
string date_str="2017a01/25";
Date date=parse_date(date_str);
cout << setw(2)<<setfill('0')<<date.day<<'.';
cout << setw(2)<<setfill('0')<<date.month<<'.';
cout << setw(4)<<setfill('0')<<date.year<<endl;
}
catch (exception& ex) {
cerr<<"Shit happens "<<ex.what()<<endl;
}
return 0;
}
```