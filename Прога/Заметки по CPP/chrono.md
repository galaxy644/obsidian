```C++
\#include<iostream>
\#include<chrono>
using namespace std;
using namespace std::chrono;
int main()
{
auto start=steady_clock::now();
int a;
cin>>a;
auto finish=steady_clock::now();
cout <<duration_cast<milliseconds>(finish-start).count();
return 0;
}
```