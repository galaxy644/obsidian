```C
\#include <stdio.h>
\#include <stdlib.h>
int cmp_int(const void * lhs, const void* rhs){
return ((*(int )lhs>=(int )rhs)-((int )lhs<=(int *)rhs));
}
//Сортируем по возрастанию.
int main()
{
int n;
scanf("%d", &n);
int vals[n];
for(int i=0;i<n;i++){
scanf("%d", &vals[i]);
}
qsort(vals,n,sizeof(int),cmp_int);
for(int i=0;i<n;i++){
printf("%d ", vals[i]);
}
return 0;
}
```