Пример класса

```C++
struct ArrayInt {
explicit ArrayInt ( size_t size )
: data_ ( new int [ size ])
, size_ ( size ) {}
~ ArrayInt () { delete [] data_ ;}
size_t size () const
{ return size_ ; }
int operator []( size_t i) const
{ return data_ [i ]; }
int & operator []( size_t i)
{ return data_ [i ]; }
...
private :
int * data_ ;
size_t size_ ;
};
```

  

[[“С” Style (Macros)]]

[[“с++” Style]]

[[Several params]]