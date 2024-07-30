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

// let是ES6中引入的新关键字，用于声明变量。它的特点包括：
// (1)块级作用域：let声明的变量具有块级作用域，这意味着它们仅在声明它们的代码块内有效。这有助于避免变量污染和命名冲突。
// (2)无变量提升：let声明的变量不会发生变量提升，即在变量声明之前使用它们会导致引用错误（ReferenceError）。(var 变量在代码执行之前就被声明)
// (3)禁止重复声明：在同一作用域内，不能使用let重复声明同一个变量。(var 允许后续重复声明覆盖前一个)
// 建议用 let 代替 var
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
```
* 对象: JavaScript的对象是一组由键-值组成的无序集合。(哈希表)
```js
// 声明
let person = {
    name: 'Bob',
    age: 20,
    tags: ['js', 'web', 'mobile'],
    city: 'Beijing',
    hasCar: true,
    zipcode: null
};
// 访问
person.name = 'Bobo';
person.age = 30;

// 访问属性是通过.操作符完成的，但这要求属性名必须是一个有效的变量名。如果属性名包含特殊字符，就必须用''括起来
let xiaohong = {
    name: '小红',
    'middle-school': 'No.1 Middle School'
};
xiaohong['middle-school']; // 'No.1 Middle School'
xiaohong['name']; // '小红'
xiaohong.name; // '小红'

// 由于JavaScript的对象是动态类型，你可以自由地给一个对象添加或删除属性
let xiaoming = {
    name: '小明'
};
xiaoming.age; // undefined
xiaoming.age = 18; // 新增一个age属性
xiaoming.age; // 18
delete xiaoming.age; // 删除age属性
xiaoming.age; // undefined
delete xiaoming['name']; // 删除name属性
xiaoming.name; // undefined
delete xiaoming.school; // 删除一个不存在的school属性也不会报错
// 检测属性是否存在
let xiaoming = {
    name: '小明',
    birth: 1990,
    school: 'No.1 Middle School',
    height: 1.70,
    weight: 65,
    score: null
};
'name' in xiaoming; // true
'grade' in xiaoming; // false
```
* 字符串: JavaScript的字符串就是用''或""括起来的字符表示。与cpp字符串操作类似。字符串不可修改，与Go语言类似。
* 数组：JavaScript的数组可以包括任意数据类型。
```js
let arr = [1, 2, 3.14, 'Hello', null, true]; // 建议方法
// 另一种创建数组的方法是通过Array()函数实现
new Array(1, 2, 3); // 创建了数组[1, 2, 3]
arr[0]; // 返回索引为0的元素，即1
arr[5]; // 返回索引为5的元素，即true
arr[6]; // 索引超出了范围，返回undefined
console.log(arr[0], arr[5], arr[6]);

// 直接给Array的length赋一个新的值会导致Array大小的变化
let arr = ['A', 'B', 'C'];
console.log(arr.length); // 3
// 调整数组大小:
arr.length = 6;
console.log(arr); // arr变为['A', 'B', 'C', undefined, undefined, undefined]
// 调整数组大小:
arr.length = 2;
console.log(arr); // arr变为['A', 'B']

// 如果通过索引赋值时，索引超过了范围，同样会引起Array大小的变化
let arr = ['A', 'B', 'C'];
arr[5] = 'x';
console.log(arr); // arr变为['A', 'B', 'C', undefined, undefined, 'x']

// slice
// slice()就是对应String的substring()版本，它截取Array的部分元素，然后返回一个新的Array
let arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
arr.slice(0, 3); // 从索引0开始，到索引3结束，但不包括索引3: ['A', 'B', 'C']
arr.slice(3); // 从索引3开始到结束: ['D', 'E', 'F', 'G']
let aCopy = arr.slice(); // ['A', 'B', 'C', 'D', 'E', 'F', 'G']

// sort()可以对当前Array进行排序，它会直接修改当前Array的元素位置，直接调用时，按照默认顺序排序
let arr = ['B', 'C', 'A'];
arr.sort();
arr; // ['A', 'B', 'C']

// push()向Array的末尾添加若干元素，pop()则把Array的最后一个元素删除掉
// unshift()向Array的头部添加若干元素，shift()则把Array的第一个元素删除掉
let arr = [1, 2];
arr.push('A', 'B'); // 返回Array新的长度: 4
arr; // [1, 2, 'A', 'B']
arr.pop(); // pop()返回'B'
arr; // [1, 2, 'A']
arr.pop(); arr.pop(); arr.pop(); // 连续pop 3次
arr; // []
arr.pop(); // 空数组继续pop不会报错，而是返回undefined

let arr = [1, 2];
arr.unshift('A', 'B'); // 返回Array新的长度: 4
arr; // ['A', 'B', 1, 2]
arr.shift(); // 'A'
arr; // ['B', 1, 2]
arr.shift(); arr.shift(); arr.shift(); // 连续shift 3次
arr; // []
arr.shift(); // 空数组继续shift不会报错，而是返回undefined
arr; // []

// splice()方法是修改Array的“万能方法”，它可以从指定的索引开始删除若干元素，然后再从该位置添加若干元素
// ** 使用 slice() 可以实现对数组的各种操作 **
let arr = ['Microsoft', 'Apple', 'Yahoo', 'AOL', 'Excite', 'Oracle'];
// 从索引2开始删除3个元素,然后再添加两个元素:
arr.splice(2, 3, 'Google', 'Facebook'); // 返回删除的元素 ['Yahoo', 'AOL', 'Excite']
arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
// 只删除,不添加:
arr.splice(2, 2); // ['Google', 'Facebook']
arr; // ['Microsoft', 'Apple', 'Oracle']
// 只添加,不删除:
arr.splice(2, 0, 'Google', 'Facebook'); // 返回[],因为没有删除任何元素
arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']

// concat()方法把当前的Array和另一个Array连接起来，并返回一个新的Array
// 请注意，concat()方法并没有修改当前Array，而是返回了一个新的Array
let arr = ['A', 'B', 'C'];
let added = arr.concat([1, 2, 3]);
added; // ['A', 'B', 'C', 1, 2, 3]
arr; // ['A', 'B', 'C']

// join()方法是一个非常实用的方法，它把当前Array的每个元素都用指定的字符串连接起来，然后返回连接后的字符串
let arr = ['A', 'B', 'C', 1, 2, 3];
arr.join('-'); // 'A-B-C-1-2-3'
```
* 哈希表(map)和集合(set)
```js
let m = new Map(); // 空Map
m.set('Adam', 67); // 添加新的key-value
m.set('Bob', 59);
m.has('Adam'); // 是否存在key 'Adam': true
m.get('Adam'); // 67
m.delete('Adam'); // 删除key 'Adam'
m.get('Adam'); // undefined

let s = new Set([1, 2, 3, 3, '3']);
s; // Set {1, 2, 3, "3"}
s.add(4);
s; // Set {1, 2, 3, 4}
s.add(4);
s; // 仍然是 Set {1, 2, 3, 4}
s.delete(3);
s; // Set {1, 2, 4}

// 遍历
for (let x of s) { // 遍历Set
    console.log(x);
}
for (let x of m) { // 遍历Map
    console.log(x[0] + '=' + x[1]);
}
```



