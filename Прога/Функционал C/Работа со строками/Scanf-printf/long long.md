Для вывода size_t можно написать так:

printf("%Iu",strchr(str,'c')-str);

  

### **Спецификаторы для платформонезависимых типов**

Вместо `"d"` в предыдущем примере будем использовать определенные стандартом константы. Как формируются их имена?

- `PRI` или `SCN` (вывод или ввода)
- Формат: `x` (шестнадцатеричный), `u` (беззнаковый), `i` или `d` (знаковый)

  

Пример:

```C
\#include <inttypes.h>
\#include <stdio.h>
void f() {
    int64_t i64 = -12;
    uint64_t u64 = 23;
    printf( "Signed 64-bit integer:   %" PRId64  "\n", i64 );
    printf( "Unsigned 64-bit integer: %" PRIu64  "\n", u64 );
    printf( "Pointer, hexadecimal     %" PRIxPTR "\n", &i64 );
    scanf( "%" SCNd64, &i64 );
    scanf( "%" SCNu64, &u64 );
}
```

  

Ниже табличка про microsoft

**Size prefixes for printf and wprintf format-type specifiers**

|   |   |   |
|---|---|---|
|To specify|Use prefix|With type specifier|
|`char``unsigned char`|`**hh**`|`**d**`, `**i**`, `**o**`, `**u**`, `**x**`, or `**X**`|
|`short int``short unsigned int`|`**h**`|`**d**`, `**i**`, `**o**`, `**u**`, `**x**`, or `**X**`|
|`__int32``unsigned __int32`|`**I32**`|`**d**`, `**i**`, `**o**`, `**u**`, `**x**`, or `**X**`|
|`__int64``unsigned __int64`|`**I64**`|`**d**`, `**i**`, `**o**`, `**u**`, `**x**`, or `**X**`|
|`intmax_t``uintmax_t`|`**j**` or `**I64**`|`**d**`, `**i**`, `**o**`, `**u**`, `**x**`, or `**X**`|
|`long double`|`**l**` (lowercase L) or `**L**`|`**a**`, `**A**`, `**e**`, `**E**`, `**f**`, `**F**`, `**g**`, or `**G**`|
|`long int``long unsigned int`|`**l**` (lowercase L)|`**d**`, `**i**`, `**o**`, `**u**`, `**x**`, or `**X**`|
|`long long int``unsigned long long int`|`**ll**` (lowercase LL)|`**d**`, `**i**`, `**o**`, `**u**`, `**x**`, or `**X**`|
|`ptrdiff_t`|`**t**` or `**I**` (uppercase i)|`**d**`, `**i**`, `**o**`, `**u**`, `**x**`, or `**X**`|
|`size_t`|`**z**` or `**I**` (uppercase i)|`**d**`, `**i**`, `**o**`, `**u**`, `**x**`, or `**X**`|
|Single-byte character|`**h**`|`**c**` or `**C**`|
|Wide character|`**l**` (lowercase L) or `**w**`|`**c**` or `**C**`|
|Single-byte character string|`**h**`|`**s**`, `**S**`, or `**Z**`|
|Wide-character string|`**l**` (lowercase L) or `**w**`|`**s**`, `**S**`, or `**Z**`|