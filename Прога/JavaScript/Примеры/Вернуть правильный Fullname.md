```js
"use strict";
/*
Передается имя и фамилия. Например ваСЯ пУпКиН.
Возвращается одна строка в правильном регистре. Например Вася Пупикн
*/
console.log(fullName("ваСЯ", "пУпКиН"));
function fullName(first, last) {
  const firstName =
    first.at(0).toLocaleUpperCase() + first.slice(1).toLocaleLowerCase();
  const lastName =
    last.at(0).toLocaleUpperCase() + last.slice(1).toLocaleLowerCase();
    return \`${firstName} ${lastName}\`;
}
`
