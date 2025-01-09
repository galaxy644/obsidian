```C++
\#include <iostream>
\#include <regex>
\#include <cassert>
using namespace std;
bool validate_phone_number_format(std::string_view str)
{
std::regex rx(R"(\+\d\(\d{3}\)\d{3}\-\d{2}\-\d{2})");
return std::regex_match(str.data(), rx);
}
int main()
{
assert(validate_phone_number_format("+7(913)123-45-67"));
assert(!validate_phone_number_format("+7(98)123-45-67"));
}
```