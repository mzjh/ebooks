I complete reading [JavaScript Enlightenment](https://www.amazon.com/JavaScript-Enlightenment-Library-User-Developer/dp/1449342884) recently. The book is more about basics in JavaScript and suitable for beginners. Here are a list of my benefits and extensions from the book.

## Math

JavaScript developers often capitalize the constructor name to distinguish the constructors from normal functions. Therefore, some developers may mistake _Math_ as function since the name is capitalized while _Math_ is really just an object.

```javascript
console.log(typeof Math); // object
console.log(typeof Array); // function
```

### Exponentiation Operator

```javascript
Math.pow(2,3) === 2 ** 3;
```

### Floor Value of a Number

```javascript
Math.floor(5.25) === 5;
~~5.25 === 5
```

## Function

There are two ways to construct a function:

- Function declaration/expression

```javascript
function sum(x, y) {
  return x + y;
}
console.log(sum(3, 4)); //7
```

- [Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function) constructor

```javascript
let multiply = new Function("x", "y", "return x * y;");
console.log(multiply(3, 4)); //12
```

In development, we often need to use [call](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call) or [apply](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) to switch the function context. E.g.

```javascript
function print() {
  console.log(this.a);
}

print.call({ a: "hello" }); //hello
```

Some interview questions will ask why _print_ doesn't define _call_ as its property but _print.call()_ won't throw error. It's because _print_ is an instance from _Function_ constructor so it inherits all the methods defined in _Function.prototype_ through [prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain).

```javascript
print.call === Function.prototype.call;
```

## How to do Array check

[typeof](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof) can be used to determine the types for primitive datatypes. But it won't be able to distinguish between arrays and objects.

```javascript
console.log(typeof [1, 2]); //object
console.log(typeof {}); //object
```

There are several wasy to do Array check:

- API: [Array.isArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)

```javascript
console.log(Array.isArray([1, 2])); //true
```

- [toString](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString)

```javascript
console.log(
  Object.prototype.toString.call([1, 2]).toLowerCase() === "[object array]"
); //true
```

Note here we have to use [Object.prototype.toString](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString) with [call](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call) to switch the calling context, as [Array.prototype.toString](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toString) is overriden.

```javascript
console.log(Object.prototype.toString.call([1, 2])); //[object Array]
console.log([1, 2].toString()); //1,2
```

- [instanceof](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/instanceof)

```javascript
[1, 2] instanceof Array === true;
```

[Object.prototype.toString](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString) won't work for custom datatypes. In this case we can use [instanceof](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/instanceof) to determine the type.

```javascript
class Person {}

let mike = new Person();
console.log(Object.prototype.toString.call(mike)); // [object Object]
console.log(mike instanceof Person); // true
```

## undefined vs null

### undefined - no value

There are two cases where a variable is undefined.

- The variable is deifned but not assigned any value.

```javascript
let s;
console.log(s); //undefined
```

- The variable is NOT defined at all.

```javascript
let obj1 = {};
console.log(obj1.a); //undefined
```

### null - special value

```javascript
let obj2 = { a: null };
console.log(obj2.a); //null
```

If we aim to filter out undefined and null, we can use _weak comparison_ with double equality sign(i.e. ==).

```javascript
console.log(null == undefined); //true
let arr = [null, undefined, 1];
let fil = arr.filter(it => {
  return it != null;
});
console.log(fil); //[1]
```

OR with `Nullish Coalescing Operator`

```javascript
const a = null;
const b = undefined;

const num1 = a ?? 1;
const num2 = b ?? 2;

console.log(num1, num2); // 1, 2
```

## Reference

[JavaScript Enlightenment](https://www.amazon.com/JavaScript-Enlightenment-Library-User-Developer/dp/1449342884)

## Notice

- If you want to follow the latest news/articles for the series of reading notes, Please [「Watch」](https://github.com/n0ruSh/the-art-of-reading)to Subscribe.
