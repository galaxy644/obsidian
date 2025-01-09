```C++
vector<string> splitstr(string str, string delimiter = " ")
{
vector<string> result;
int start = 0;
int end = str.find(delimiter);
while (end != -1) {
result.push_back( str.substr(start, end - start));
start = end + delimiter.size();
end = str.find(delimiter, start);
}
result.push_back( str.substr(start, end - start));
return result;
}
```