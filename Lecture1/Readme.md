# Lecture1 JavaScript Basic
## Outline
- Overview
- JavaScript
  - Variable
  - s

## Overview
- 設計師:水龍頭樣式
- 前端:安裝水龍頭與水管
- 後端:提供水管水

## variable
### undefined
```js
console.log(hello);
// 不會跳出 alert
// console 會 show error, 寫 hello is not defined
```
```js
var hello;
console.log(hello);
// 不會有error，畫面會成功跳出 alert
// 但訊息中 hello 的值是 undefined
```
```js
var hello;
hello = 5;
console.log(hello);
// 不會有error，畫面會成功跳出 alert, 訊息是 5
```

### 變數有效範圍
變數都有自己有效範圍，變數如果沒有用 `var` 宣告的話，會自動變成全域變數，所以要很注意在function裡面的變數會不會把外面的變數弄髒掉。

### Types
- Primitive types
  - number
  - string
  - boolean
  - null
  - undefined
- Object types
  - 所有非 Primitive types 都屬於物件

### Primitive types V.S Object types
- Primitive types
  - 以值作為比較
    ```js
    123 === 123 // true
    '5xruby' === '5xruby' //true
    ```
  - property 是唯讀的不能改
    ```js
    var str = '5xruby';
    str.length  // 6

    str.length = 10;
    str.length // 6
    ```
- Object types
  - 以 reference 來比較
    ```js
    var obj = {}; // undefined
    var obj2 = {}; // undefined
    obj === obj2; // false

    obj2 = obj;
    obj == obj2; // true
    ```
  - property 可以變動
    ```js

    ```

### NaN (Number type)
是數字，但是有物件的特性，用 isNaN() 來判斷說是不是 NaN
```js
var n = 0/0; // NaN
n === NaN;   // false
typeof n;    // "number"
isNaN(n);    // true
```

### String
可以用單雙引號包起來，也可以用 `+`連接

#### escape
需要顯示單雙引號時，可以用跳脫字元
```js
var str = "What's This."; // OK
str = 'What's This.';     // error
str = 'What\'s This.';    // OK
```
#### prompt
```js
var number = prompt('輸入0~9', '');
```
prompt 回傳的都是字串

#### 自動轉型
```js
var age = 30;

age = age + ""; // "30", age 被自動轉換成字串
age = age + 1;  // "301", 1 被自動轉換成字串
age = age * 2;  // 602, 被自動轉換成 number
```
字串的 `+` 比數字 `+` 優先順序高，所以只要是數字和字串相加，數字都會被轉換成字串，而不是字串轉成數字。

#### null v.s. undefined
- undefined 是此變數還沒有給值
- null 此變數確定沒有值，是我們主動 assign 給變數告知其就是沒有值
```js
Number(null) // 0
Number(undefined) // NaN
```

### Array
#### basic operation
```js
var color = ["red", "yellow", "blue"];

color.length; // 3
color.push("orange"); // ["red", "yellow", "blue", "orange"];
color.shift(); // ["yellow", "blue", "orange"];
color.pop();   // ["yellow", "blue"];
```
#### traverse
```js
colors.forEach(function(element, index, array){
  console.log("  " + index + "      " + element);
});
```
#### indexOf
```js
var colors = [ "red", "yellow", "blue"];            
console.log( colors.indexOf("red") );     // 0
console.log( colors.indexOf("black") );   // -1
```

### Object
```js
var people = {
  name: "Kuro",
  age: 30,
  skills:{
     frontend: ["HTML", "CSS", "JavaScript"],
     backend:  ["PHP", "ASP.net", "nod]e.js"]
   },
   sayHello: function(){ alert('hello'); }
};
// get value
alert( people.name );
alert( people['name'] );
// set value  
people.name = 'John';
//  if key in this object          
console.log( 'skills' in people );  // true
console.log( 'level' in people );   // false
//  delete key in this object       
delete people.age;
```

Javacript 的物件
```js
var Obj = { x:1 }; // { x:1 } 是 instance, Obj 是 name
var Obj2 = { x:1 };
Obj === Obj2; //false

Obj2 = Obj;
Obj === Obj2; //true

// 當一個 instance 沒有被任何 name 指到時
// 瀏覽器會判斷沒有被任何 name 指導，瀏覽器會自己把它清掉。
```

## Decision Structures and Operator
### `==` v.s `===`
- `==`: 數值相等
- `===`: 數值跟型別都相等
- `!=`: 數值不相等
- `!==`: 數值不相等或型別不相等

因為 javascript 會自動轉換型別，所以比較上建議都用 `===`

### Ternary `?`
```js
if ( 5 > 3)? "bigger" : "smaller"
```
### Logical operator
- `&&` and
- `||` or
- `!` not
### If-else
```js
if (condition A) {
  //condition    A ...
} else if (condition B) {
  //condition    B ...
} else if (condition C) {
  //condition    C ...
} else {
  //condition          
}
```
### Switch Case
```js
switch ( season ) {
  case 1:
    alert("春");
  break;

  case 2:
    alert("夏");
  break;

  case 3:
    alert("秋");
    break;
  case 4:
    alert("冬");
  break;

  default:
    alert("數值有錯");
  break;
```

## Math
```js
Math.ceil() // 無條件進位
Math.floor() // 無條件捨去
Math.round() // 四捨五入
```
## Loop
for
```js
for (i=0; i<10; i++) {
  console.log(i);
}
```
while
```js
var i=0;
while (i<10) {
  console.log(i);
  i++;
}
```
