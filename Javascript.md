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
#### 变量提升



