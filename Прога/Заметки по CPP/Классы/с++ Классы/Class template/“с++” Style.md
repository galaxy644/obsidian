```C++
template <class Type >
struct Array {
explicit Array ( size_t size )
: data_ ( new Type [ size ])
, size_ ( size ) {}
~ Array ()
{ delete [] data_ ; }
size_t size () const
{ return size_ ; }
Type operator []( size_t i) const
{ return data_ [i ]; }
Type & operator []( size_t i)
{ return data_ [i ]; }
...
private :
Type * data_ ;
size_t size_ ;
};
```

```C++
int main ()
{
Array <int > ai (10);
Array <float > af (20);
...
return 0;
}
```