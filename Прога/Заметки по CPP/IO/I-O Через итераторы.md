```C++
\#include<iostream>
\#include<iterator>

int main(){
std::ios_base::sync_with_stdio(0);
auto it=std::istream_iterator<int>(std::cin);
std::size_t n=*it++;
long long sum=0;
while(n--) sum+=*it++;
std::cout<<sum;
return 0;
}
```