```js
"use strict";
function transformArrToObject(arr){
const obj = {};
    for (const prop of arr) {
        obj[prop.name]=prop.value;
        console.log(prop.name,prop.value);
    }
return obj;
}

function transformArrToObject2(arr) {
    const res = {};
    arr.forEach((i) => res[i.name] = i.value);
    return res;
}

const arr = [
    {name: "name",value:"Анатолий"},
    {name: "age",value: 40},
];

console.log(transformArrToObject(arr));
```
