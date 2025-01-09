```C++
\#include <iostream>
\#include <regex>
\#include <cassert>
\#include <vector>
using namespace std;
std::vectorstd::string extract_tokens_from_string(std::string const& str)
{
std::regex rx(R"(\w+)");
std::smatch match;
std::vectorstd::string results;
for (auto i = std::sregex_iterator(std::cbegin(str), std::cend(str), rx);
i != std::sregex_iterator(); ++i)
{
// if ((*i)[1].matched)
//какая то непонятная хрень
results.push_back(i->str());
}
return results;
}
int main()
{
string str = "aaa bbb ccc,zz";
std::vector<string> result = extract_tokens_from_string(str);
cout << "size = " <<result.size()<<endl;
for (auto s : result)
cout << s << " ";
return 0;
}
```