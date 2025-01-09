```C
\#include <stdio.h>
\#include <stdlib.h>
int main()
{
int h,m;
const char * str="21:22";
sscanf(str,"%d:%d",&h,&m);
printf("%d %d\n",h,m);
//
printf("%ld\n",strtol("f",NULL,16));
//
//попробуем контролировать ошибки. вторым аргументом передаем указатель,
//В который функция будет писать первый невалидный симвод
char * finish;
//Эта строка явно невалидная с точки зрения 10-ной системы.
const char * str2="aaa3bbb";
long x= strtol(str2,&finish,10);
if(str2==finish){
printf("Not a number\n");
}
else{
printf("%ld___%s\n",x,finish);
}
//
return 0;
}
```