```C++
\#include <iostream>
\#include <cstdarg>
using namespace std;
double average(int n, ...) {
int sum = 0;
va_list p;
va_start(p, n);
for (int i = 0; i < n; ++i) {
sum += va_arg(p, int);
}
va_end(p);
return (double)sum/n;
}
int main() {
cout<<average(3,5,7,12)<<" "<<average(5,1,8,3,2,-5);
return 0;
}
```