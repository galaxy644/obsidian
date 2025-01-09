**Конструктор Копирования** принимает в качестве аргумента ссылку на такой же объект

```C++
struct IntArray{
explicit IntArray (size_t sz):
size_(sz),
data_(new int[sz]) {}
~IntArray(){
delete [] data_;
}
//Вспомогательный метод, чтобы было удобно писать конструктор присвоения
void  swap(IntArray &a){
std::swap(size_, a.size_);
std::swap(data_, a.data_);
}
// Конструктор копирования
IntArray(IntArray const& a){
size_=a.size_;
data_=new (std::nothrow)int[size_];
// Предпочительно пользовать copy&swap http://www.gotw.ca/gotw/059.htm
if(data_){ //Проверка на nullptr, если память не выделилась
for(size_t i=0;i!=size_;++i){
data_[i]=a.data_[i];
}
}
}
// Конструктор присваивания
IntArray & operator =(IntArray const& a){
if (this != &a){
IntArray(a).swap(*this); //создаем временную копию (IntArray a) с помощью констр. копирования. И потом меняем ее местами с
}
return *this; // вот так возсращается ссылка на текущий экз. объекта. Важно !
}
bool setval(size_t n,int val){
if(n<size_){
*(data_+n)=val;
return true;
}else
return false;
}
// Позволяет получить указатель на i-й элемент
int & getval(const size_t n) {
return *(data_+n);
}
// Позволяет получить значение приватного поля size
size_t size() const {
return size_;
}
private:
size_t size_;
int* data_;
};
// Просто удобный оператор для вывода структуры целиком
ostream&  operator << (ostream& stream, IntArray & arr){
for(size_t i=0;i<arr.size();i++){
stream<<arr.getval(i)<<" ";
}
return stream;
}
```