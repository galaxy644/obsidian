\#include <iostream>  
\#include <vector>  
\#include<windows.h>  
using namespace std;  

int main ()  
{  
HANDLE hConsole=GetStdHandle(STD_OUTPUT_HANDLE);  
SetConsoleTextAttribute(hConsole,12);  
cout<<"RUSSIA"<<endl;  
return 0;  
}