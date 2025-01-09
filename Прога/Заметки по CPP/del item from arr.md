```C++
\#include <iostream>
using namespace std;
template <typename T>
void initArray(T array[], size_t sz) {
int* tempPtr = array;
for (auto i = 0; i < sz; i++, tempPtr++) {
tempPtr = rand() % 11 - 5;
}
}
template <typename T>
void printArray(T array[], size_t sz) {
int tempPtr = array;
int maxpos = 0, minpos = 0;
for (auto i = 0; i < sz; i++) {
cout << tempPtr[i] << " ";
}
cout << endl;
}
template <typename T>
void transformArray(T* &array, size_t &sz) {
int cnt=0;
for (auto i = 0,j=0; i < sz; i++) {
if (array[i] == 0)
cnt++;
}
T* newarray = new T[sz-cnt];
for (auto i = 0,j=0; i < sz; i++) {
if (array[i] != 0){
newarray[j++]=array[i];
}
}			
delete[] array;
array=newarray;
sz-=cnt;
}
```

```C++
int main() {
setlocale(LC_ALL, "rus");
int salt, * ptrInt = NULL;
size_t n;
cin >> n>>salt;
ptrInt = new int[n];
srand(salt);
initArray(ptrInt, n);
printArray(ptrInt, n);
transformArray(ptrInt, n);
printArray(ptrInt, n);
delete[] ptrInt;
ptrInt = NULL;
return 0;
}
```