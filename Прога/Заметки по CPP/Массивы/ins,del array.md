```C++
\#include <iostream>
using namespace std;
template <typename T>
void initArray(T array[], int sz) {
	int* tempPtr = array;
	for (auto i = 0; i < sz; i++, tempPtr++) {
		*tempPtr = rand() % 26 - 10;
	}
}
template <typename T>
void printArray(T array[], int sz) {
	int* tempPtr = array;
	int maxpos = 0, minpos = 0;
	for (auto i = 0; i < sz; i++) {
		cout << tempPtr[i] << " ";
	}
	cout << endl;
}
template <typename T>
void addElement(T *&array, int &n){
	T* newarray = new T[n+1];
	int pos;
	T val;
	cin>>pos>>val;
	if(pos<1)
		pos=1;
	if(pos>n)
		pos=n+1;
	for(int i=0;i+1<pos;i++)
		newarray[i]=array[i];
	newarray[pos-1]=val;
	for(int i=pos;i<=n;i++)
		newarray[i]=array[i-1];
	delete[] array;
	array=newarray;
	n++;
}
template <typename T>
void delElement(T *&array, int &n){
	T* newarray = new T[n-1];
	int pos;
	cin>>pos;
	if(pos<1||pos>n)
		return;
	for(int i=0;i<pos;i++)
		newarray[i]=array[i];
	for(int i=pos-1;i+1<n;i++)
		newarray[i]=array[i+1];
	delete[] array;
	array=newarray;
	n--;
	}
int main(){
	int n,beg;
	cin>>n>>beg;
	srand(beg);
	int *a=NULL;
	a=new int[n];
	initArray(a,n);
	printArray(a,n);
	int k;//выбор пользователя
	while(true){ //бесконечный цикл
		cin>>k;//ввод выбранного варианта
		switch(k){
			case 1: addElement(a,n); break; //1 - добавление элемента
			case 2: delElement(a,n); break; //2 - удаление элемента
			case 3: printArray(a,n); break; //3 - печать массива
			default: delete[] a; return 0; //другие числа - окончание работы программы
		}
	}
}
```