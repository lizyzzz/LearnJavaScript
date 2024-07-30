## JavaScript
### 0. 基本语法
除了赋值语句与cpp不相同，其他语法大同小异。
```js
var a; // 申明了变量a，此时a的值为undefined
var $b = 1; // 申明了变量$b，同时给$b赋值，此时$b的值为1
var s_007 = '007'; // s_007是一个字符串
var Answer = true; // Answer是一个布尔值true
var t = null; // t的值是null
var x = 1;
x = 2;
console.log('hello javascript');
```
### 1.数据类型
* Number: 不区分整数和浮点数，统一用Number表示，以下都是合法的Number类型，Number可以直接做四则运算，规则和数学一致
```js
123; // 整数123
0.456; // 浮点数0.456
1.2345e3; // 科学计数法表示1.2345x1000，等同于1234.5
-99; // 负数
NaN; // NaN表示Not a Number，当无法计算结果时用NaN表示
Infinity; // Infinity表示无限大，当数值超过了JavaScript的Number所能表示的最大值时，就表示为Infinity

1 + 2; // 3
(1 + 2) * 5 / 2; // 7.5
2 / 0; // Infinity
0 / 0; // NaN
10 % 3; // 1
10.5 % 3; // 1.5

// Number不区分整数和浮点数
12.00 === 12

// 要精确表示比253还大的整数，可以使用内置的BigInt类型，它的表示方法是在整数后加一个n
// 也可以使用BigInt()把Number和字符串转换成BigInt
// 使用BigInt可以正常进行加减乘除等运算，结果仍然是一个BigInt，但不能把一个BigInt和一个Number放在一起运算
var bi1 = 9223372036854775807n;
var bi2 = BigInt(12345);
var bi3 = BigInt("0x7fffffffffffffff");

// 数组: JavaScript的数组可以包括任意数据类型
[1, 2, 3.14, 'Hello', null, true]; // 建议方法
// 另一种创建数组的方法是通过Array()函数实现
new Array(1, 2, 3); // 创建了数组[1, 2, 3]
arr[0]; // 返回索引为0的元素，即1
arr[5]; // 返回索引为5的元素，即true
arr[6]; // 索引超出了范围，返回undefined
console.log(arr[0], arr[5], arr[6]);
```
* 对象: JavaScript的对象是一组由键-值组成的无序集合。(哈希表)
```js
var person = {
    name: 'Bob',
    age: 20,
    tags: ['js', 'web', 'mobile'],
    city: 'Beijing',
    hasCar: true,
    zipcode: null
};
```

* 字符串: 
