# javascript 基础语法

## 递增运算符

1. 前置自增和后置自增如果单独使用，效果是一样的

2. 前置自增口诀：先自加1，后返回值

   ```javascript
   var a = 10;
   ++a; // ++a = 11 a = 11
   var b = ++a + 2; // a = 12 ++a = 12
   console.log(b) // 14
   ```
   
   后置自增口诀：先表达式返回值，后自加1
   
   ```javascript
   var c = 10;
   c++; // c++ = 11 c = 11
   var d = c++ + 2; // c++ = 11 c = 12
   console.log(d); // 13
   ```

## 短路运算（逻辑中断）

> 当有多个表达式（值）时，左边的表达式值可以确定结果时，就不再继续运算右边的表达式的值。

1. 逻辑与（&&）短路运算

   语法：表达式1 && 表达式2

   如果表达式1结果为真，则返回表达式2

   如果表达式1结果为假，则返回表达式1

   ```javascript
   console.log(123 && 456) // 456
   console.log(0 && 1+2) // 0
   // 如果有空的或者否定的则为假：0、undefined、null、NaN
   ```

2. 逻辑或（||）短路运算

   语法：表达式1 || 表达式2

   如果表达式1结果为真，则返回表达式1

   如果表达式1结果为假，则返回表达式2

   ```javascript
   console.log(123 || 456) // 123
   console.log(0 || 1+2) // 3
   ```

## 冒泡排序   

   ```javascript
var arr = [5,4,3,2,1];
   ```

   案例分析

1. 一共需要的趟数，我们用外层for循环

   ​     5个数据我们一共需要4趟

   ​     长度就是 arr.length - 1

   ​	第一趟 4 3 2 1 5

   ​	第二趟 3 2 1 4 5

   ​	第三趟 2 1 3 4 5

   ​	第四趟 1 2 3 4 5

2. 每一趟交换次数我们用里层for循环

   ​	第一趟 交换4次

   ​	第二趟 交换3次

   ​	第三趟 交换2次

   ​	第四趟 交换1次

   ​	长度就是 数组长度 减去 次数

   ​	但是我们次数是从0开始的 所以 arr.length - i - 1

3. 交换2个变量

 ```javascript
// 利用用函数封装冒泡排序
function sort(arr){
    for (var i = 0; i <= arr.length - 1; i++) { //外层循环管趟数
        for (var j = 0; j <= arr.length - i - 1; j++) { //里层循环管 每一趟的次数
            // 内部交换2个变量的值 前一个和后一个数组元素相比较
            if (arr[j] > arr[j + 1]) {
                var temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    return arr;
}
var arr2 = sort([999, 9, 99]);
console.log(arr2); // [9,99,999]
 ```

## 作用域链

   作用域链：内部函数访问外部函数变量的机制，用链式查找决定取哪些数据能被内部访问，称之为作用域链。（就近原则）

   ```javascript
   function f1(){ // 外部函数
       var num = 123;
       function f2(){ // 内部函数
           console.log(num) 
       }
   }
   var num = 456;
   fn(); //123
   ```

   

 ## 预解析

   1. 我们js引擎运行js分为两步：预解析、代码执行
   
      （1）预解析 js引擎会把js代码里面所有的 var 还有 function 提升到当前作用域的最前面。
   
      （2）代码执行 按照代码书写的顺序从上往下执行
   
   2. 预解析分为 变量预解析（变量提升）和函数预解析（函数提升）
   
      （1）变量提升 就是把所有的变量声明提升到当前最前面 不提升赋值操作
   
      （2）函数提升 就是把所有的函数声明提升到当前最前面 不提升函数
   
      ```javascript
      function f1(){
          //变量提升
          // var a;
          // a = 9; b = 9; c = 9;
          var a = b = c = 9;
          //相当于 var a = 9; b = 9; c = 9; b和c直接赋值，没有var声明 当全局看
          console.log(a); //9
          console.log(b); //9
          console.log(c); //9
      }
      f1();
      console.log(c); //9
      console.log(b); //9
      console.log(a); //报错
      
      ```
   
      

## 构造函数

```javascript
// 1.构造函数名字首字母要大写
// 2.构造函数不需要return语句 就可以返回结果
// 3.我们调用构造函数必须使用 new
// 4.只要new Star()调用函数创建一个对象
// 5.我们的属性和方法前面要加一个this
function Star(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
}
// 对象
var ldh = new Star('刘德华', 18, '男'); //调用函数返回的是一个对象
console.log(ldh.name);
console.log(ldh['sex']);
```



## 查阅JS对象方法

   ### MDN

   学习一个内置对象的使用，只要学会常用成员的使用即可，我们可以通过查文档学习，可以通过MDN/W3C来查询。

   MDN：(https://developer.mozilla.org/zh-CN/)

   如何学习对象中的方法？

   1. 查阅该方法的功能
   
   2.  查看里面参数的意义和类型
   
   3. 查看返回值的意义和类型
   
   4. 通过demo进行测试
   
      

## Math 对象

### 三个取整方法

* Math.floor() 向下取整 往最小了取值

  ```javascript
  console.log(Math.floor(1.1)); // 1
  console.log(Math.floor(1.5)); // 1
  ```

* Math.ceil() 向上取整 往最大了取值

  ```javascript
  console.log(Math.ceil(1.1)); // 2
  console.log(Math.ceil(1.5)); // 2
  ```

* Math.round() 四舍五入 其他数字都是四舍五入，但是 .5 特殊，它往大了取

  ```javascript
  console.log(Math.round(1.1)); // 1
  console.log(Math.round(1.5)); // 2
  console.log(Math.round(-1.1)); // -1
  console.log(Math.round(-1.5)); // 这个结果是 -1
  ```



### Math对象随机数方法

Math.random() 返回一个随机的小数 0  =<   x  <  1

案例

```javascript
// 得到两个数之间的整数，包括两个数在内
function getRandom(min, max) {
	return Math.floor(Math.random() * (max - min + 1) + min); //含最大值，含最小值
}
// 随机点名
var arr = ['王五', '张三疯', '李四', '丽丽', '小明'];
console.log(arr[getRandom(0, arr.length - 1)]);
// 猜数字游戏
var random = getRandom(1, 10);
while (true) { // 死循环
	var num = prompt('你猜？输入1~10之间的数字');
    if (num > random) {
		alert('你猜大了');
	} else if (num < random) {
		alert('你猜小了')
	} else {
		alert('你好帅哦，猜对了');
		break; // 退出循环
	}
}


```

## Date对象

Date对象是一个构造函数，必须使用new来调用创建的日期对象。

格式化日期

```javascript
// 我们写一个 2020年3月3号 星期二
var date = new Date();
var year = date.getFullYear(); // 返回当前年份
var month = date.getMonth() + 1; // 月份 返回的月份小1个月 月份要+1
var dates = date.getDate() // 返回的是 几号
var weekArr = ['星期天', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六']
var day = date.getDay(); // 周一返回的是1 周六返回的是6 但是 周日返回的是0
console.log('今天是：' + year + '年' + month + '月' + dates + '日 ' + weekArr[day]);
```



获得总的毫秒数（时间戳）不是当前的毫秒数，而是距离1970年1月1日过了多少毫秒

```javascript
// 1.通过valueOf() getTime()
var date = new Date();
console.log(date.valueOf());
console.log(date.getTime());
// 2.简单的写法 （最常用的写法）
 var date1 = +new Date(); // +new Date() 返回的就是总的毫秒数
 console.log(date1);
// 3.H5新增的 获得总的毫秒数
console.log(Date.now());
```



倒计时效果

```javascript
// 时间戳转换为天、时、分、秒
// d = parseInt(总秒数 / 60 / 60 / 24); // 计算天数
// h = parseInt(总秒数 / 60 / 60 % 24); // 计算小时
// m = parseInt(总秒数 / 60 % 60); // 计算分数
// s = parseInt(总秒数 % 60); // 计算当前秒数
function countDown(time) {
	var nowTime = +new Date(); // 返回的是当前总的毫秒数
	var inputTime = +new Date(time); // 返回的是用户输入的总的毫秒数
	var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数
	var d = parseInt(times / 60 / 60 / 24); // 天
	d = d < 10 ? '0' + d : d;
	var h = parseInt(times / 60 / 60 % 24); // 时
    h = h < 10 ? '0' + h : h;
 	var m = parseInt(times / 60 % 60); // 分
 	m = m < 10 ? '0' + m : m;
	var s = parseInt(times % 60); // 秒
	s = s < 10 ? '0' + s : s;
	return d + '天' + h + '时' + m + '分' + s + '秒';
}
console.log(countDown('2020-3-4 21:00:00'));
```

## 数组对象

检测是否为数组

```javascript
// (1). instanceof 运算符 它可以用来检测是否为数组
var arr = [];
var obj = {};
console.log(arr instanceof Array); // true
console.log(obj instanceof Array); // false
// (2) Array.isArray(参数) H5新增的语法 ie9+以上版本支持 
console.log(Array.isArray(arr)); // true
console.log(Array.isArray(obj)); // false
```



数组去重（重要案例）

```javascript
// 1.目标：把旧数组里面不重复的元素取出放到新数组中，重复的元素只保留一个，放到新数组中去重
// 2.核心算法：我们遍历数组，拿着旧数组的元素去查询新数组，如果该元素在新数组里面没有出现过，我们就添加，否则不添加
// 3.我们怎么知道该元素有没有存在？利用 新数组.indexOf(数组元素) 如果返回-1，就说明新数组里面没有该元素
function unique(arr){
    var newArr=[];
    for(var i = 0; i < arr.length; i++){
        if(newArr.indexOf(arr[i]) === -1){
            newArr.push(arr[i]);
        }
    }
    return newArr;
}
var demo = unique(['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b']);
console.log(demo); // ['c','a','z','x','b']
```



 数组转换为字符串

1. Array.toString()

2. Array.join(分隔符)



Array.splice(修改的开始位置,[移除数组元素的个数],[要添加的元素])

* 通过删除或替换现有元素或者原地添加新的元素来修改数组

* 此方法会改变原数组

* 如果只删除了一个元素，则返回只包含一个元素的数组，如果没有删除元素，则返回空数组。

```javascript
var fish = ['a', 'b', 'c', 'd'];
var removed = fish.splice(0, 2, 'g', 'h');
console.log(removed); // 被删除的元素：['a','b'] 
console.log(fish); // 运算后的fish：['g','h','c','d']
```



查找数组中某个元素出现的次数

```javascript
// 在['red','blue','red','green','pink','red']中，求 red 出现的位置和次数
// 核心算法：先查找第一个出现的位置
// 然后 只要indexOf返回的结果不是 -1 就继续往后查找
// 因为indexOf只能查找第一个，所以后面的查找，一定是当前的索引加1，从而继续查找
var colors = ['red', 'blue', 'red', 'green', 'pink', 'red'];
var index = colors.indexOf('red'); // 第一个red出现的位置
var n = 0;
for (var i = 0; i < colors.length; i++) {
	if (index !== -1) {
 		console.log('red出现的位置在：'+index);
        n++;
		index = colors.indexOf('red', index + 1);
 	}
}
console.log('red出现的次数是：' + n);
```

## 字符串对象

字符串操作方法

1. concat(str1,str2,str3,...) 用于连接两个或多个字符串。拼接字符串，等效于 + ，+ 更常用

2. substr(start,length) 从 start 位置开始（索引号），length 取的个数  重点记住这个

   ```javascript
   var str = '改革春风吹满地';
   console.log(str.substr(2,2)); // 春风
   ```

3. 替换字符 replace('被替换的字符','替换为的字符')

   ```javascript
   // 有一个字符串 'abcoefoxyozzopp' 要求把里面所有的 o 替换为 *
   var str1 = 'abcoefoxyozzopp';
   while (str1.indexOf('o') !== -1) {
   	str1 = str1.replace('o', '*');
   }
   console.log(str1);
   ```

4. 字符转换为数组 split('分隔符')   （我们之前学的join('分隔符') 是把数组转换为字符串

   ```javascript
   var str2 = 'red,blue,green';
   console.log(str2.split(',')); // ['red','blue','green']
   var str3 = 'a&b&c';
   console.log(str3.split('&')); // ["a", "b", "c"]
   ```

## 简单数据类型和复杂数据类型

1. 值类型：简单数据类型/基本数据类型，在存储时变量中存储的时值本身，因此叫做值类型

   string , number , boolean , undefined , null

   ```javascript
   // 简单数据类型 null 返回的时一个空的对象 object 
   var timer = null;
   console.log(typeof timer);
   // 如果有个变量我们以后打算存储为对象，暂时没想好放哈，这个时候就跟给 null
   // 1. 简单数据类型 是放在栈里面 里面直接开辟一个空间存放的是值
   // 2. 复杂数据类型 首先在栈里面存放地址 十六进制表示 然后这个地址指向堆里面的数据
   
   ```

2. 引用类型：复杂数据类型，在存储变量中存储的仅仅是地址（引用），因此叫做引用数据类型

   通过 new 关键字创建的对象（系统对象，自定义对象），如 Object , Array , Date 等

   ```javascript
   // 函数的形参也可以看做是一个变量，当我们把引用类型变量传给形参时，其实是把变量在栈空间里保存的堆地址赋值给了形参，形参和实参其实保存的是同一个地址，所以操作的是同一个对象。
   function Person(name) {
   	this.name = name;
   }
   function f1(x) { //x = p
   	console.log(x.name); // 2. 这个输出什么？
   	x.name = '张学友';
    	console.log(x.name); // 3. 这个输出什么？
   }
   var p = new Person('刘德华');
   console.log(p.name); // 1. 这个输出什么？
   f1(p);
   console.log(p.name); // 4. 这个输出什么？
   ```

   

![负责类型传参](E:\Personal\ZQwork\note\JS\images\复杂数据类型传参.PNG)