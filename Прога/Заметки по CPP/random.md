```Bash
\#include <iostream>
\#include <random>
int main(){
// случайные значения
const int maxval=1024;
std::random_device seed;
std::mt19937 engine(seed());
std::uniform_int_distribution<> uniformDist(0, maxval);
for(int i=0;i<50;i++){
std::cout<<uniformDist(engine)<<std::endl;
}
return 0;
}
```