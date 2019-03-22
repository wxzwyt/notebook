#  Javascript  
## 快速入门
### 基本语法
1. 使用 `===` 不使用 `==`  
2. `NaN`不等于任何值,包括本身( `Not a Number` )  
3. 使用 `isNaN(NaN)` 判断
4. 浮点数比较 `1/3 === (1-2/3); //false` 应比较 `Math.abs(1/3 - (1-2/3)) < 0.0000001; //true`
5. `null` 表示"空"(值), `''`表示长度为0的字符串, `undefined`表示值未定义
6. 显示变量的内容 `console.log(x)`  
7. 多行字符串用 ` `` `表示  
8. 多个字符串连接用 `${name}, ${age}` 来表示
### 字符串操作  
1. 对字符串某个索引赋值不会有任何效果  
2. `toUpperCase()` 将字符串转换为大写  
3. `toLowerCase()` 将字符串转换为小写  
4. `indexOf()` 搜索指定字符串出现的位置  
5. `substring()` 返回指定索引区间的子串  
### 数组  
1. `arr.length` 返回数组长度, 对其赋值会改变`arr` 大小  
2. 可通过索引赋新值, 但索引超出范围会引起`arr` 大小的变化  
3. 通过`indexOf()` 来搜索指定元素的位置  
4. `slice()` 对应`String` 的`substring()`, 截取`arr` 的部分元素, 然后返回一个新的`Array`, 不给`slice()` 传递参数, 可以复制`arr`  
5. `push()` 向`Array` 末尾添加若干元素, `pop()` 删除最后一个元素  
6. `unshift()` 往`Array` 头部添加元素, `shift()` 删除头部第一个元素  
7. `sort()` 对`Array` 进行排序, 并修改当前`Array` 的元素位置  
8. `reverse()` 反转整个`Array`  
9. `splice()` 从指定的索引开始删除若干元素,再添加若干元素  
10. `concat()` 将两个`Array` 连接起来  
11. `join()` 将`Array` 中的每个元素都用指定的字符串连接起来 eg:`arr.join('-')`  
### 对象  
1. 对象用键值对方式存储数据, eg:```var xiaoming = {
    name: '小明',
    birth: 1990,
    school: 'No.1 Middle School',
    height: 1.70,
    weight: 65,
    score: null
};```  
2. 末尾不加`,` , 避免有的IE的版本不识别  
3. 通过`.` 来访问属性  
4. 访问一个不存在的属性返回`undefined`  
5. 可自由给对象添加 (`xiaoming.age;  xiaoming.age=18;`) 或删除 (`delete`) 属性  
6. 检测对象是否拥有某一属性,用`in` (`'name' in xiaoming;  // true`) , `in` 判断一个属性存在,这个属性可能是继承的属性  
7. 用 `hasOwnProperty()` 判断属性是否是继承得到的  
### 条件判断  
1. `if () {...} else {...}`  
2. JavaScript把`null`、`undefined`、`0`、`NaN`和空字符串`''`视为`false`，其他值一概视为`true`  
### 循环  
1. `for`  
2. `for ... in` `for (var key in o) {...}`  
3. `for ... in` 可以直接循环出`Array`的索引,得到的是`String`  
4. `while`  
5. `do { ... } while()` (循环至少执行1次,而`for`和`while`可能一次都不执行)  
### Map&Set  
#### Map  
1. `{}`可视为其他语言中的`Map`或`Dictionary`(一对键值对),但键必须是字符串  
2. `var m = new Map([['Michael', 95], ['Bob', 75], ['Tracy', 85]]);`或
```
    var m = new Map(); // 空Map
    m.set('Adam', 67); // 添加新的key-value
    m.set('Bob', 59);
```  
3. 一个`key`只能对应一个`value`, 给`key`赋多个值时, 后面的值会把前面的冲掉  
#### Set  
1. `set`和`map`类似,是一组key的集合  
2. `add()`  
3. `delete()`  
### iterable  
1. `Array` `Map` `Set`都属于`iterable`类型, 此类型可以通过`for ... of`循环来遍历  
2. `for ... of`只循环集合本身的元素  
3. `forEach()`,`Set`没索引,回调函数的前两个参数是其本身
    ```
        var s = new Set(['A', 'B', 'C']);
        s.forEach(function (element, sameElement, set) {
        console.log(element);
        });
    ```  
    `Map`回调函数参数为`value` `key` `map`  
    ```
        var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
        m.forEach(function (value, key, map) {
        console.log(value);
        });
    ```  
4. 对某些参数不感兴趣,JavaScript的函数调用不要求参数必须一致  
## 函数  
### 函数定义和调用  
1. 定义:  
```
function abs(x) {
    if (x >= 0) {
        return x;
    } else {
        return -x;
    }
}
```  
2. 函数如果无`return`语句,返回`undefined`  
3. JavaScript的函数也是一个对象,第二种定义方式:  
```
    var abs = function (x) {
        if (x >= 0) {
            return x;
        } else {
            return -x;
        }
    };
```
结尾需要加`;`
#### 调用函数  
1. 按顺序传入参数
2. 传入多个参数也不影响调用结果  
3. 传入的参数少也没问题
#### *!*arguments
1. 只在函数内部起作用，并且永远指向当前函数的调用者传入的所有参数
#### rest
1. `function foo(a,b, ...rest) {...}`, `rest`只能写在最后, 前面用`...`标识
### 变量作用域与解构赋值
1. 不同函数内的同一变量互不影响
2. 内层函数可以访问外层函数定义的变量,反过来则不行
#### *!*变量提升
1. **在函数内部首先声明所有变量**
#### 全局作用域
1. 不在任何函数内定义的变量就具有全局作用域
2. JS默认有一个全局对象`window`, 全局作用域的变量被绑定到`window`的一个属性
3. 顶层函数的定义也被视为一个全局变量
4. `alert()`也是`window`的一个变量
5. **JavaScript实际上只有一个全局作用域。任何变量（函数也视为变量），如果没有在当前函数作用域中找到，就会继续往上查找，最后如果在全局作用域中也没有找到，则报ReferenceError错误**
#### 名字空间
将代码全部放入唯一的名字空间,可以减少冲突
#### 局部作用域
1. `for`循环等语句块中无法定义具有局部作用的变量
2. `let`替代`var`可以声明一个块级作用域的变量
#### 常量
1. `let`和`var`声明的是变量,声明常量用全部大写的变量(ES6前)
2. `const`来定义常量(ES6)
3. `const`和`let`都具有块级作用域
#### *!*解构赋值
1. eg:
```
    'use strict';
    // 如果浏览器支持解构赋值就不会报错:
    var [x, y, z] = ['hello', 'JavaScript', 'ES6'];
    // x, y, z分别被赋值为数组对应元素:
    console.log('x = ' + x + ', y = ' + y + ', z = ' + z);
```
2. 对数组元素进行解构赋值,多个变量用`[...]`括起来(对于有嵌套的对象属性进行赋值时,需保证对应层次一致)
3. 解构赋值可以忽略某些元素
4. 从一个对象中取出若干属性,也可以使用解构赋值
5. 如果对应的属性不存在, 变量将被赋值为`undefined`, **注意:变量名和属性名不一样使用`:`**, eg:`let {passport:id} = person;`就可以取出id值
6. 解构赋值还可以使用默认值,这样不会返回`undefined`
7. 解构赋值可以简化代码
### 方法
1. eg:
```
    var xiaoming = {
        name: '小明',
        birth: 1990,
        age: function () {
            var y = new Date().getFullYear();
            return y - this.birth;
        }
    };
```
此例里,`age()`为一个方法
2. 避免`this`坑, 用`var that = this`捕获`this
3. 运用`apply()`方法,可以指定函数的`this`指向哪个对象,`apply()`方法的第一个参数为需要绑定的`this`变量,第二个参数是`Array`,表示函数本身
4. `call()`与`apply()`类似, `apply()`将参数打包成`Array`再传入, `call()`把参数按顺序传入
5. 对于普通函数调用,通常把`this`绑定为`null`
6. *!*装饰器
### 高阶函数 (Array)
1. 编写高阶函数,就是让函数的参数能够接收别的函数
```
    function add(x, y, f) {
        return f(x) + f(y);
    }
    var x = add(-5, 6, Math.abs); // 11
```  
#### map/reduce
1. `Array.map()`, 传入参数为函数对象本身
2. `Array.map()`, 把结果继续和序列的下一个元素做累积计算
#### filter (筛选/过滤)
1. `filter()`把传入的函数依次作用于每个元素, 再根据返回值`true or false`来决定是否保留该元素
2. 接收的回调函数可以有多个参数, 通常只使用第一个参数`element`(Array的某个元素), 还可以接收另外两个参数(index, self)
#### sort
1. `sort()`先转换为`String`, 再进行排序
2. `sort()`是高阶函数, 可接收一个比较函数来实现自定义排序 
### 闭包



