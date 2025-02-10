
```js
"use strict";
function getFrequentlyRepeatedSymbol(str){
const lettersCount={};
    for (const letter of str.toLocaleLowerCase()) {
        if(lettersCount[letter]){
            lettersCount[letter]++;
        }else{
            lettersCount[letter]=1;
        }
    }
 

const repeatedSymbol={
    symbol:null,
    repeated:0,
};

for (const key in lettersCount) {
    if(repeatedSymbol.repeated<lettersCount[key]){
        repeatedSymbol.symbol=key;
        repeatedSymbol.repeated=lettersCount[key];
        }
}
return repeatedSymbol.symbol;
}

function getFrequentlyRepeatedSymbol2(str) {
    let res = ["", 0];
    for (let i of str) {
      const reg = new RegExp(i, "gi");
      const count = (str.match(reg) || []).length;
      res = (count > res[1]) ? [i, count] : res;
    }
    return res[0];
  }

console.log(getFrequentlyRepeatedSymbol2("AaabBbbc"));
```
