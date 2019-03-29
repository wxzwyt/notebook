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
### *!*闭包
1. eg:  
```
    function lazy_sum(arr) {
        var sum = function () {
            return arr.reduce(function (x, y) {
                return x + y;
            });
        }
        return sum;
    }
```  
调用`lazy_sum()`返回求和函数, 调用`f()`时, 返回结果.  
2. 每次调用都会返回一个新的函数, 返回函数不要引用任何循环变量, 或后续会发生变化的变量  
3. *!* **匿名函数**  
    `(function (x) { return x * x }) (3)`  
4. 可实现私有变量
### 箭头函数
1. `x => x * x`相当于`function (x) { return x * x }`, 相当于匿名函数  
2. 箭头函数完全修复了this的指向, this总是指向词法作用域
### generator
1. 一边循环一边计算
2. `function*`还可以用`return`或`yield`
3. `for ... of`循环迭代generator对象, 不需自己判断`done`  
## 标准对象
1. 不使用`new Number()`, `new Boolean()`, `new String()`创建包装对象
2. 用`parseInt()`或`parseFloat()`来转换任意类型到`number`
3. 用`String()`来转换任意类型到`string`, 或直接调用某个对象的`toString()`方法
4. 通常不必把任意类型转换为`boolean`再判断, 可直接写`if (myVar) {...}`
5. `typeof`操作符可以判断`number`, `boolean`, `string`, `function`, `undefined`
6. 判断`Array`使用`Array.isArray(arr)`
7. 判断`null`使用`myVar === null`
8. 判断某个全局变量是否存在用`typeof window.myVar === 'undefined'`
9. 函数内部判断某个变量是否存在用`typeof myVar === 'undefined'`
### Date
1. `Date`对象用来表示日期和时间, eg:  
```
var now = new Date();
now; // Wed Jun 24 2015 19:49:22 GMT+0800 (CST)
now.getFullYear(); // 2015, 年份
now.getMonth(); // 5, 月份，注意月份范围是0~11，5表示六月
now.getDate(); // 24, 表示24号
now.getDay(); // 3, 表示星期三
now.getHours(); // 19, 24小时制
now.getMinutes(); // 49, 分钟
now.getSeconds(); // 22, 秒
now.getMilliseconds(); // 875, 毫秒数
now.getTime(); // 1435146562875, 以number形式表示的时间戳
```
2. JavaScript的`Date`对象月份值从0开始，牢记0=1月，1=2月，2=3月，……，11=12月。 
3. `Date.parse()`返回时间戳, 传入的字符串使用实际月份01~12, eg:  
```
var d = Date.parse('2015-06-24T19:49:22.875+08:00');
d; // 1435146562875
```
4. 将时间戳转换为`Date`, 转换为`Date`后`getMonth()`获取月份值为0~11, eg:  
```
var d = new Date(1435146562875);
d; // Wed Jun 24 2015 19:49:22 GMT+0800 (CST)
d.getMonth(); // 5
```
5. `Date`对象表示的时间总是按浏览器所在时区显示的,使用`toLocalString()`显示本地时间, `使用toUTCString()`显示UTC时间
### RegExp(正则表达式)(`\`表示转义)
1. `\d`可以匹配一个数字, `\w`可以匹配一个字母或数字, `.`可以匹配任意字符, `\s`可以匹配一个空格(Tab也算)
2. `*`表示任意个字符, `+`表示至少一个字符, `?`表示0或1个字符, `{n}`表示n个字符, `{n,m}`表示n-m个字符
3. [0-9a-zA-Z\_]可以匹配一个数字、字母或者下划线
4. [0-9a-zA-Z\_]+可以匹配至少由一个数字、字母或者下划线组成的字符串
5. [a-zA-Z\_\$][0-9a-zA-Z\_\$]*可以匹配由字母或下划线、$开头，后接任意个由一个数字、字母或者下划线、$组成的字符串，也就是**JavaScript允许的变量名**
6. [a-zA-Z\_\$][0-9a-zA-Z\_\$]{0, 19}更精确地限制了变量的长度是1-20个字符（前面1个字符+后面最多19个字符）
7. `A|B`可以匹配A或B, `^`表示行的开头, `$`表示行的结束, eg: `^\d`表示必须以数字开头, `\d$`表示必须以数字结束
8. js创建正则表达式, `/正则表达式/`或`new RegExp('正则表达式')`, eg:  
```
var re1 = /ABC\-001/;
var re2 = new RegExp('ABC\\-001');
```
9. `test()`方法测试给定的字符串是否符合条件
10. 正常切分代码无法识别连续的字符串, 使用正则表达式则可以, eg:
```
'a b   c'.split(/\s+/); // ['a', 'b', 'c']
'a,b;; c  d'.split(/[\s\,\;]+/); // ['a', 'b', 'c', 'd']
```
11. 可以提取子串, 用`()`表示要提取的分组, 正则表达式定义了组,则可使用`exec()`方法提取出子串来, 匹配成功后, 返回一个`Array`, 第一个元素为整个字符串, 后面元素为匹配成功的子串
12. 正则匹配默认是贪婪匹配, 组的末尾加`?`即可实现非贪婪匹配
13. `g`表示全局匹配, 可多次执行`exec()`方法来搜索一个匹配的字符串, 可指定`i`标志, 表示忽略大小写, `m`标志, 表示执行多行匹配
### JSON
1. JSON序列化输出`JSON.stringify()`, 第一个参数为对象名, 第二个参数用于控制如何筛选对象的键值(指定输出属性,传入`Array []`), 第二个参数还可以传入一个函数, 这样每个键值对都会被函数先处理, eg:  
```
JSON.stringify(xiaoming, ['name', 'skills'], '  ');
```
2. 精确控制序列化, 可定义一个`toJSON()`方法, 直接返回JSON应该序列化的数据, eg:  
```
toJSON: function () {
        return { // 只输出name和age，并且改变了key：
            'Name': this.name,
            'Age': this.age
        };
    }
```
3. JSON格式的字符串,直接使用`JSON.parse()`将其变成JS对象, 还可以接收一个函数, 用来转换解析出的属性
## 面向对象编程
1. 通过原型(prototype)而不是类和实例来实现面向对象编程
2. eg:
```
var Student = {
    name: 'Robot',
    height: 1.2,
    run: function () {
        console.log(this.name + ' is running...');
    }
};

var xiaoming = {
    name: '小明'
};

xiaoming.__proto__ = Student;
```
3. **不要直接使用`obj.__proto__`去改变一个对象的原型**
4. 普通函数加`new`变成构造函数, 构造函数绑定的`this`指向新创建的对象, 并默认返回`this`(不需要在最后写`return this;`)
5. 使用`new Student()`创建的对象还从原型上获取了一个`constructor`属性, 指向函数`Student`本身
6. **构造函数首字母大写, 普通函数首字母小写**
7. 可编写`createStudent()`函数, 在内部封装所有的`new`操作, 其优点:
    - 不需要`new`来调用  
    - 参数非常灵活(可直接用JSON创建一个对象)
### 原型继承
原型继承的实现方式:
 - 定义新的构造函数, 并在内部用`call()`调用希望继承的构造函数, 并绑定`this`
 - 借助中间函数`F`事项原型链继承, 最好通过封装的`inherits`函数来完成
 - 继续在新的构造函数的原型上定义新方法
### class继承
`class` `extends`
## 浏览器
### 浏览器对象
1. `window` 不仅充当全局作用域,还表示浏览器窗口
    - 有`innerWidth`和`innerHeight`属性, 可以获取浏览器窗口的内部宽度和高度
    - 还有`outerWidth`和`outerHeight`属性, 可以获取浏览器窗口的整个宽高
2. `navigator` 浏览器的信息, (**信息可以很容易地被用户修改**) 常用属性:  
    - `navigator.appName`: 浏览器名称
    - `appVersion`: 浏览器版本
    - `language`: 设置的语言
    - `platform`: 操作系统类型
    - `userAgent`: 浏览器设定的`User-Agent`字符串
3. `screen` 屏幕的信息  
    - `screen.width`: 屏幕宽度(以像素为单位)
    - `screen.height`: 屏幕高度
    - 'colorDepth': 返回颜色位数
4. `location` 当前页面的URL信息  
    - `location.href`: 获取完整的URL
    -   ```
        location.protocol; // 'http'  
        location.host; // 'www.example.com'  
        location.port; // '8080'  
        location.pathname; // '/path/index.html'  
        location.search; // '?a=1&b=2'  
        location.hash; // 'TOP'  
        ```
    - `location.assign()`: 加载一个新页面
    - `location.reload()`: 重载当前页面
5. `document` 当前页面, `document`是整个DOM树的根节点  
    - `title`: 从HTML文档中的`<title>xxx</title>`读取的, 也可以动态改变
    - `getElementById()`和`getElementsByTagName()`可按ID获得一个DOM节点和按Tag名称获得一组DOM节点
    - `cookie`: 获取当前页面的Cookie(设定`httpOnly`的Cookie将不能被JavaScript读取)
6. `history` 保存浏览器的历史记录(**应该废弃**)
    - `back()`或`forward()`, 相当于用户点击了浏览器的"后退"或"前进"按钮
### 操作DOM
1. DOM是一个树形结构, 有以下几个操作:  
    - 更新: 更新该DOM节点的内容
    - 遍历: 遍历该DOM节点下的子节点
    - 添加: 在该DOM节点下新增一个子节点
    - 删除: 将该节点从HTML中删除
2. 拿节点:
    - `getElementById()`, `getElementsByTagName()`, `getElementsByClassName()`
    - `querySelector()`, `querySelectorAll()`
#### 更新DOM
1. 修改节点的文本:
    - 修改`innerHTML`属性(不但可以修改一个DOM节点的文本内容, 还可以直接通过HTML片段修改DOM节点内部的子树), eg:  
    ```
        // 获取<p id="p-id">...</p>
        var p = document.getElementById('p-id');
        // 设置文本为abc:
        p.innerHTML = 'ABC'; // <p id="p-id">ABC</p>
        // 设置HTML:
        p.innerHTML = 'ABC <span style="color:red">RED</span> XYZ';
        // <p>...</p>的内部结构已修改
    ```
    - 修改`innerText`或`textContent`属性(在读取属性时, `innerText`不返回隐藏元素的文本, `textContent`返回所有文本), eg:  
    ```
        // 获取<p id="p-id">...</p>
        var p = document.getElementById('p-id');
        // 设置文本:
        p.innerText = '<script>alert("Hi")</script>';
        // HTML被自动编码，无法设置一个<script>节点:
        // <p id="p-id">&lt;script&gt;alert("Hi")&lt;/script&gt;</p>
    ```
    - CSS中的`font-size`在JavaScript中为`fontSize`
#### 插入DOM
1. 如果DOM节点是空的, 可以直接用`innerHTML = '<span>child</span>'`即可修改DOM节点, (不为空则不能这么做,那样`innerHTML`会替换掉原来的所有子节点)
2. `appendChild` 将一个子节点添加到父节点的最后一个子节点(多数时候从零创建一个新的节点,然后插入到指定位置), eg:  
    ```
        var
            list = document.getElementById('list'),
            haskell = document.createElement('p');
        haskell.id = 'haskell';
        haskell.innerText = 'Haskell';
        list.appendChild(haskell)
    ```
3. `insertBefore`, `parentElement.insertBefore(newElement, referenceElement);`, 子节点会插入到`referenceElement`之前(重点是拿到"参考子节点"的引用, 通常循环一个父节点的所有子节点, 可以通过迭代`children`属性实现), eg:
    ```
        var
            list = document.getElementById('list'),
            ref = document.getElementById('python'),
            haskell = document.createElement('p');
        haskell.id = 'haskell';
        haskell.innerText = 'Haskell';
        list.insertBefore(haskell, ref);
    ```
#### 删除DOM
1. 首先获得该节点本身和其父节点, 再调用父节点的`removeChild`把自己删掉
2. `children`属性是一个只读属性, 随时在变化
### 操作表单
1. HTML表单的输入控件:  
    - 文本框(`<input type="text">`)
    - 口令框(`<input type="password">`)
    - 单选框(`<input type="radio">`)
    - 复选框(`<input type="checkbox">`)
    - 下拉框(`<select>`)
    - 隐藏文本(`<input type="hiden">`)
2. 获取了`<input>`节点的引用, 就可直接调用`value`获取对应的用户输入值, eg:  
    ```
        // <input type="text" id="email">
        var input = document.getElementById('email');
        input.value; // '用户输入的值'
    ```
    可应用于`text`, `password`, `hidden`, `select`
3. 对于单选框和复选框, `value`属性返回HTML预设的值, 使用`checked`判断是否勾选上了
4. `text`, `password`, `hidden`, `select`可以直接设置`value`
5. 单选框和复选框, 设置`checked`为`true`或`false`
6. 通过`<form>`元素的`submit()`方法提交表单(扰乱了浏览器对form的正常提交)
7. 响应`<form>`的`onsubmit`事件, 在提交form时作修改, eg:  
    ```
        <!-- HTML -->
        <form id="test-form" onsubmit="return checkForm()">
        <input type="text" name="test">
        <button type="submit">Submit</button>
        </form>

        <script>
        function checkForm() {
            var form = document.getElementById('test-form');
            // 可以在此修改form的input...
            // 继续下一步:
        return true;
        }
        </script>
    ```
    `return true`来告诉浏览器继续提交
8. 在检查和修改`<input>`时, 充分利用`<input type="hidden">`来传递数据
### 操作文件
1. 上传文件时, JS仅在提交表单时对文件扩展名做检查,防止用户上传无效格式的文件
2. JS是单线程执行模式, 执行多任务实际上是异步调用
### AJAX
1. 写AJAX主要依靠`XMLHttpRequest`对象
2. 当创建了`XMLHttpRequest`对象后，要先设置`onreadystatechange`的回调函数。在回调函数中，通常我们只需通过`readyState === 4`判断请求是否完成，如果已完成，再根据`status === 200`判断是否是一个成功的响应
3. `XMLHttpRequest`对象的`open()`方法有3个参数，第一个参数指定是GET还是POST，第二个参数指定URL地址，第三个参数指定是否使用异步，默认是true
4. [AJAX](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/001434499861493e7c35be5e0864769a2c06afb4754acc6000)
5. JS发送AJAX请求时, URL的域名必须和当前页面完全一致
6. JS请求外域方法:  
    - 通过Flash插件发送HTTP请求(可绕过浏览器的安全限制)
    - 通过在同源域名下架设一个代理服务器来转发, js负责把请求发送到代理服务器, 代理服务器再把结果返回
    - JSONP, 只能用GET请求, 并要求返回JS, 通常以函数调用的形式返回
### *!*Promise
## JQuery
1. JQuery解决的问题:  
    - 消除浏览器差异
    - 间接的操作DOM的方法
    - 轻松实现动画, 修改CSS等操作
2. 使用JQuery, 只需在页面的`<head>`引入JQuery文件即可, eg:  
    ```
    <head>
    <script src="//code.jquery.com/jquery-1.11.3.min.js"></script>
    ...
    </head>
    ```
3. $
### 选择器
1. `$('#dom-id')`
