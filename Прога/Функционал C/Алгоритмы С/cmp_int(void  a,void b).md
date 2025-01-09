```C
\#include <stdio.h>
\#include <stdlib.h>
int cmp_int(const void * lhs, const void* rhs){
if(*(int )lhs==(int )rhs)
return 0;
else if((int )lhs<(int *)rhs)
return -1;
else
return 1;
}
//
int main()
{
int x, y, res;
scanf("%d%d", &x, &y);
res = cmp_int(&x, &y);
if (res < 0)
res = '<';
else if (res > 0)
res = '>';
else
res = '=';
printf("%c\n", res);
return 0;
}
```

А вот так очень красиво

```C
int cmp_int(const void * lhs, const void* rhs){
    return ((*(int *)lhs>=*(int *)rhs)-(*(int *)lhs<=*(int *)rhs));
}
```

Или еще проще:

```C
int cmp_int(const void * lhs, const void* rhs){
    return ((*(int *)lhs>*(int *)rhs)-(*(int *)lhs<*(int *)rhs));
}
```