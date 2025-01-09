```C++
\#include <iostream>
\#include <vector>
\#include <map>
using namespace std;
string hex2bin(string str){
string result;
map<char,string> h2b={{'0',"0000"},{'1',"0001"},{'2',"0010"},{'3',"0011"},{'4',"0100"},
{'5',"0101"},{'6',"0110"},{'7',"0111"},{'8',"1000"},{'9',"1001"},
{'A',"1010"},{'B',"1011"},{'C',"1100"},{'D',"1101"},{'E',"1110"},
{'F',"1111"}};
for(size_t i=0;i<str.size();i++){
result+=h2b.at(str.at(i));
}
size_t pos=result.find("1");
result.erase(0,pos);
if(result.size()==0)
result="0";
return result;
}
```

```C++
string bin2oct(string str){
string result;
map<string,char> b2o={{"000",'0'},{"001",'1'},{"010",'2'},{"011",'3'},
{"100",'4'},{"101",'5'},{"110",'6'},{"111",'7'}};
while(((str.size())%3)!=0)
str='0'+str;
for(size_t i=0;i<str.size()/3;i++){
string oct=str.substr(i*3,3);
result+=b2o.at(oct);
}
return result;
}
```

```C++
int main ()
{
string str;
cin>>str;
cout<<bin2oct(hex2bin(str));
return 0;
}
```