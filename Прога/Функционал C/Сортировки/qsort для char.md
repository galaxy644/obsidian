Напечатайте входную строку, отсортировав ее по **возрастанию** ASCII кода символов, с помощью стандартной функции **qsort.** Дана строка длиной не более 1000 символов. Первая точка - конец последовательности символов, которую надо отсортировать. **Точку сортировать не нужно. Все, что находится после первой точки - игнорировать.** Напечатайте отсортированную строку **с точкой в конце**.

```C
\#include <stdio.h>
\#include <stdlib.h>
\#define MAXCHARS 1000
int cmp_char_decr(const void * lhs, const void* rhs){
return ((*(char )lhs>=(char )rhs)-((char )lhs<=(char *)rhs));
}
int main()
{
char *vals=malloc(MAXCHARS);
char temp;
int j=0;
	while ((temp = getchar()) != '.'){
		vals[j]=temp;
		j++;
	}
//Не будем вводить всю строку. Все равно выводить ее не понадобится.
//Да и в задании явно нигде не прописано, что нужно всю строку вводить.
qsort(vals,j,sizeof(char),cmp_char_decr);
for(int i=0;i<j;i++){
		printf("%c", vals[i]);
}
free(vals);
printf(".\n");
return 0;
}
```