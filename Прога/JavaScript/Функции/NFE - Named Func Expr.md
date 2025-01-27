Named functional expression
Нужно для того, чтобы название функции можно было использовать внутри функции, вызываемой рекурсивно

например:
"use strict";
const sumNums = function<b> fn</b> ( from,to){
	if (from>to){
		return 0;
	}
	 else {
	 return (from+ <b>fn</b>( from + 1 , to ));
	 }
}

const result=sumNums( 2 ,5 );
console.log(result);
