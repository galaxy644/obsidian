Решение через макросы в стиле “C”

```C++
\#define DEFINE_ARRAY ( Name , Type )\
struct Name { \
explicit Name ( size_t size ) \
: data_ ( new Type [ size ]) \
, size_ ( size ) {} \
~ Name () { delete [] data_ ; } \
\
size_t size () const \
{ return size_ ; } \
\
Type operator []( size_t i) const \
{ return data_ [i ]; } \
Type & operator []( size_t i) \
{ return data_ [i ]; } \
... \
private : \
Type * data_ ; \
size_t size_ ; \
}
```

Дальнейшее использование

```C++
DEFINE_ARRAY ( ArrayInt , int );
DEFINE_ARRAY ( ArrayFlt , float );
int main ()
{
ArrayInt ai (10);
ArrayFlt af (20);
...
return 0;
}
```