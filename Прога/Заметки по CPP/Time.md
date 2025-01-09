```C++
\#include<iostream>
using namespace std;
struct Time{
int days;
int hours;
int minutes;
int seconds;
Time(){}
Time(int days, int hours, int minutes, int seconds)
: days(days), hours(hours), minutes(minutes), seconds(seconds)
{}
Time(long long t) {
days = int((t < 0 ? t - 86399 : t) / 86400); // в случ. отр. t округ вниз (a-b+1)/b
t = int((t % 86400 + 864000) % 86400); // универсальн. формула привед. к положит. остатку
hours = t / 3600 % 24;
minutes = t / 60 % 60;
seconds = t % 60;
}
long long inSeconds() {
return ((days * 24LL + hours) * 60 + minutes) *60 + seconds;
}
};
```

```C++
Time operator + (Time lhs, Time rhs){
Time result{lhs.days+rhs.days,lhs.hours+rhs.hours,lhs.minutes+rhs.minutes,lhs.seconds+rhs.seconds};
if (result.seconds>=60){
result.minutes++;
result.seconds-=60;
}
if (result.minutes>=60){
result.hours++;
result.minutes-=60;
}
if (result.hours>=24){
result.days++;
result.hours-=24;
}
return result;
}
Time operator - (Time lhs, Time rhs){
Time result{lhs.days-rhs.days,lhs.hours-rhs.hours,lhs.minutes-rhs.minutes,lhs.seconds-rhs.seconds};
if (result.seconds<0){
result.minutes--;
result.seconds+=60;
}
if (result.minutes<0){
result.hours--;
result.minutes+=60;
}
if (result.hours<0){
result.days--;
result.hours+=24;
}
return result;
}
ostream & operator << (ostream &stream, const Time& time){
return stream << time.days<<" "<<time.hours<<" "<<time.minutes<<" "<<time.seconds<<endl;
}
istream & operator >> (istream &stream, Time& time){
stream>>time.days>>time.hours>>time.minutes>>time.seconds;
return stream;
}
int main() {
Time t1,t2;
cin>>t1>>t2;
cout<<(t1-t2);
return 0;
}
```

решение от Глозмана. Очень элегантно

```C
struct my_time {
int day, hour, minute, second;
```

```C++
my_time()
{}

my_time(int day, int hour, int minute, int second)
    : day(day), hour(hour), minute(minute), second(second)
    {}

my_time(long long t) {
    day = int((t < 0 ? t - 86399 : t) / 86400); // в случ. отр. t округ вниз (a-b+1)/b
    t = int((t % 86400 + 864000) % 86400); // универсальн. формула привед. к положит. остатку
    hour = t / 3600 % 24;
    minute = t / 60 % 60;
    second = t % 60;
}

friend my_time operator -(my_time &t1, my_time &t2) {
    return my_time(t1.inSeconds() - t2.inSeconds());
}

long long inSeconds() {
    return ((day * 24LL + hour) * 60 + minute) *60 + second;
}

friend std::ostream& operator<<(std::ostream& strm, const my_time& t)
{
    strm << '[' << t.day << " " << t.hour << " " << t.minute << " " << t.second << ']' << endl;
    return strm;
}
};
```