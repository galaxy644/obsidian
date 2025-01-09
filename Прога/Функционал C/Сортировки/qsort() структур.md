Для типа struct Point, хранящей целочисленные координаты точки на плоскости  
struct Point {  
int x;  
int y;  
};  
Реализуйте функцию  
int cmp_Point(const void * p1, const void * p2)  
которая сравнивает две точки, хранящихся как struct Point, лежащих по адресам p1 и p2 и возвращает:  
0 - если точки лежат на равном расстоянии от центра координат,  
< 0 - если первая ближе второй от центра координат,  

0 - если первая дальше второй от центра координат.  
Посылать только реализацию функции. Для её проверки используется код:  
  

```C
int main()
{
struct Point a, b;
scanf("%d%d", &a.x, &a.y);
scanf("%d%d", &b.x, &b.y);
int res = cmp_Point(&a, &b);
if (res < 0)
printf("<\n");
else if (res > 0)
printf(">\n");
else
printf("=\n");
return 0;
}
```

```C
//Решение задачи
\#include <stdio.h>
\#include <stdlib.h>
\#include <math.h>
struct Point {
    int x;
    int y;
};
//
int cmp_Point(const void * p1, const void * p2){
const struct Point *P1=(struct Point*) p1;
const struct Point *P2=(struct Point*) p2;
float dist1=hypot(abs(P1->x),abs(P1->y));
float dist2=hypot(abs(P2->x),abs(P2->y));
return (dist1>=dist2)-(dist1<=dist2);
}
int main()
{
    struct Point a, b;
    scanf("%d%d", &a.x, &a.y);
    scanf("%d%d", &b.x, &b.y);
    int res = cmp_Point(&a, &b);
    if (res < 0)
        printf("<\n");
    else if (res > 0)
        printf(">\n");
    else
        printf("=\n");
    return 0;
}
```