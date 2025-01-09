\#include <iostream>  
\#include <string>  
\#include <string_view>  
int main(){  
//setlocale(LC_ALL, "rus"); // корректное отображение Кириллицы  
std::cout << std::endl;  
char arr[] {"abcdef"};  
std::string_view digits("123456789");  
std::cout<<digits.substr(0,4)<<std::endl;  
std::string_view letters{arr};  
std::cout<<letters.substr(0,4)<<std::endl;  
digits.remove_prefix(1);  
digits.remove_suffix(1);  
std::cout<<static_cast  
std::string(digits)<<std::endl;  
return 0;