# Lecture 2
- Function

## Function
複習有兩種宣告方式
```js
// 宣告以後才能使用
var sum = function (a, b, c) {
  return a + b + c;
};

// 全域
function sum (a, b, c) {
  return a + b + c;
};
```

## Callback
當我們執行某個 function 時，會希望這個 function 可以去執行另外一個function，被執行的function，我們會叫做 callback function。
```js
for( var i = 0; i < 5; i++ ){ 
  window.setTimeout( 
    function(){ console.log(i); }, 
    1000);
}
// 5
// 5
// 5
// 5
// 5
```
會先在瀏覽器的 stack 塞了五個 task 說 "一秒鐘後要印 i"，一秒鐘之後，因為i已經是5了，這五個task開始印就會印出5

## IIFE 
Immediately Invoked Function Expression.
```js
for( var i = 0; i < 5; i++ ) {  //   i       
  (function(i){
    window.setTimeout( 
      function(){ console.log(i); }, 
      1000 * i);
  })(i);
}
```

## Closure
延長 function 裡面的變數週期

先看沒有 Closure
```js
function doSome() {
  var x = 10;
  function f(y) {
    return x + y;
}
return f; }
var foo = doSome();
console.log( foo(20) ); // 30
console.log( foo(30) ); // 40
// 30 // 40
```
使用 Closure
```js
function doSome() {
  var x = 10;
  function f(y) {
    x = x + y;
    return x;
}
return f; }
var foo = doSome(); // f裡的 x 變 10
console.log( foo(20) ); // 30, f 裡的 x 會更新成/保留為 30
console.log( foo(30) ); // 60...  
```

## DOM Tree