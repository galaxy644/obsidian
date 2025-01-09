возможны следующие способы описания двумерного массива как параметра функции:

1) как двумерный массив с фиксированным числом столбцов:

```C++
void initArray(int mas[][M], int n){...}
```

2) как указатель на массив-строку (опять же массив с фиксированным числом элементов):

```C++
void printArray(int(*mas)[M], int n){...}
```

3) передать  в функцию указатель на нулевой элемент массива, количество  строк и количество столбцов. При этом в алгоритме функции мы используем тот факт, что двумерный массив располагается в памяти подряд, строка за строкой.

```C++
int sumOfArray(int *mas, int n, int m) {...}
```

Вызов такой функции должен быть таким:

```C++
sumOfArray(&a[0][0], N, M)
```

Либо таким:

```C++
sumOfArray(a[0], N, M)
```

  

**Пример.** Инициализировать двумерный массив размерности 3 на 4 случайными числами от -5 до 5, вывести его на консоль. Подсчитать сумму элементов массива.

```C++
\#include <iostream>
\#include <time.h>
\#define N 3
\#define M 4
using namespace std;
//инициализация двумерного массива случайными числами
void initArray(int mas[][M], int n)
{
	for (int i = 0; i<n; i++)
		for (int j = 0; j<M; j++)
			mas[i][j] = rand() % 11 - 5;
}
//вывод двумерного массива на консоль в виде таблицы
void printArray(int(*mas)[M], int n)
{
	for (int i = 0; i<n; i++)
	{
		for (int j = 0; j<M; j++)
			cout << mas[i][j] << "\t";
		cout << "\n";
	}
}
//подсчет суммы элементов массива
//работа с двумерным массивом как с одномерным
int sumOfArray(int *mas, int n, int m)
{
	int sum = 0;
	for (int i = 0; i<n; i++)
		for (int j = 0; j<m; j++)
		{
			sum += *mas;
			mas++;
		}
	return sum;
}
void main()
{
	setlocale(LC_ALL, "rus");
	int a[N][M];
	srand(time(0));
	initArray(a, N);
	printArray(a, N);
	cout << "Сумма элементов массива=" << sumOfArray(&a[0][0], N, M) << "\n";
	system("pause");
}
```

Еще один пример работы с 2d массивами

```C++
\#include <iostream>
\#include <iomanip>
\#define    MIN_ELEM    -10
\#define    MAX_ELEM    10
\#define    ARRAY_SIZE    15
\#define    COL    5
\#define    ROW    4
using namespace std;
void fillArray(int a[][COL],int row,int col,int salt){
int range=MAX_ELEM-MIN_ELEM;
srand(salt);
for(int i=0;i<row;i++){
for( int j=0;j<col;j++)
a[i][j]=rand()%(range+1)+MIN_ELEM;
}
}
void printArray(int a[][COL],int row,int col){
for(int i=0;i<row;i++){
for( int j=0;j<col;j++)
cout<<a[i][j]<<"\t";
cout<<endl;
}
```

```C++
}
int main() {
int salt;
int a[ROW][COL];
cin>>salt;
fillArray(a,ROW,COL,salt);
printArray(a,ROW,COL);
return 0;
}
```