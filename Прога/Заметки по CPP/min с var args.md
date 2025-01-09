Функция нахождения минимума с переменным числом аргументов

```C++
template <typename T>
T minimum(T const a, T const b) { return a < b ? a : b; }
template <typename T1, typename... T>
T1 minimum(T1 a, T... args)
{
return minimum(a, minimum(args...));
}
int main()
{
cout<<  minimum(5.3, 4.1, 2.22, 3.8);
}
```

  

```C++
template <class Compare, typename T>
T minimumc(Compare comp, T const a, T const b)
{ return comp(a, b) ? a : b; }
template <class Compare, typename T1, typename... T>
T1 minimumc(Compare comp, T1 a, T... args)
{
return minimumc(comp, a, minimumc(comp, args...));
}
int main()
{
auto y = minimumc(std::less<>(), 3, 2, 1, 0);
}
```

```C++
int main()
{
auto y = minimumc(std::less<>(), 3, 2, 1, 0);
}
```