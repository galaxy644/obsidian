```C++
unsigned nth_power(unsigned x,unsigned n){
unsigned acc=1;
if( (x<2) || (n==1) ) return x;
while (n>0){
if( (n&0x1)==0x1 ){
//if( (n%2)==1 ){
acc*=x;
n-=1;
}
else{
x*=x;
n/=2;
}
}
return acc;
}
```