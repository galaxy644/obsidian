To return the string from the function, you should either do static allocation or dynamic allocation  
For example,  

```C++
char* return_string_using_static_allocation() {
static char s[] = "static allocation of string";
return s;
}
char* return_string_using_dynamic_allocation() {
char* s = malloc(100 * sizeof(char));
s = "dynamic allocation of string";
return s;
}
```