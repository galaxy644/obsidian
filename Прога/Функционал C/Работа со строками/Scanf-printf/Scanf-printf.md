Как напечатать n символов из строки ? "%*.*s", указать минимальную и максимальную длины во время выполнения - более реалистично в сценарии, подобном:

```Plain
printf("Data: %*.*s Other info: %d\n", minlen, maxlen, string, info);
```

Как прочитать scanf в переменную строку символов:

You can take a string as input in C using `scanf(“%s”, s)`. But, it accepts string only until it finds the first space.

In order to take a line as input, you can use `scanf("%[^\n]%*c", s);` where  is defined as `char s[MAX_LEN]` where  is the maximum size of . Here, `[]` is the scanset character. `^\n` stands for taking input until a newline isn't encountered. Then, with this `%*c`, it reads the newline character and here, the used `*` indicates that this newline character is discarded.

**Note:** The statement: `scanf("%[^\n]%*c", s);` will not work because the last statement will read a newline character, `\n`, from the previous line. This can be handled in a variety of ways. One way is to use `scanf("\n");` before the last statement.

  

```C
//Читаем по слову и выводим результат.
int main() {
char s[1001];
     while(1 == scanf("%1000s", s)) {
      printf("%s\n", s);
      }
}
```

Читаем строку с клавиатуры до символа “\n”

```C
\#include <stdio.h>
int main() {
char a[10];
while (fgets(a, 10, stdin)!=NULL) {
printf("%s\n", a);   // печатаем прочитанное
}
return 0;
}
```

  

char*p;

scanf(”%ms”,&p); //”%ms” неявный вызов malloc

free(p);

Сокровища флинта

  

```C
\#include <stdio.h>
\#include <string.h>
int main(void){
char a[11];
int ox=0,oy=0,n;
while (scanf("%10s%d",&a,&n)==2) {
if (0 == strcmp(a, "North"))
oy+=n;
else if (0 == strcmp(a, "South"))
oy-=n;
else if (0 == strcmp(a, "East"))
ox+=n;
else if (0 == strcmp(a, "West"))
ox-=n;
}
printf("%d %d",ox,oy);
return 0;
}
```

  

[[Спецификаторы формата]]

[[long long]]