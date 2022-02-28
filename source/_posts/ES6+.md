---
title: 'ES6+'
data:  '2022-1-22 17:14:06'
tags:  
- 教程
- 新特性
- 前端
description: '什么是 ECMA、什么是 ES6、ECMA相关概念、ES6到ES11新特性的简单介绍、以ES6为主'
cover: https://klcxy.top/oss-manage-service/ossinfo/queryOssUrl?tbOssInfo.oiid=385
---****



## 1.    简介
### 1.1什么是 ECMA

![](https://bkimg.cdn.bcebos.com/pic/faedab64034f78f040ee982971310a55b2191c06?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U4MA==,g_7,xp_5,yp_5/format,f_auto)
ECMA（European Computer Manufacturers Association）中文名称为欧洲计算机制
造商协会，这个组织的目标是评估、开发和认可电信和计算机标准。1994 年后该
组织改名为 Ecma 国际。
### 1.2什么是 ES6
ECMAScript 6.0（以下简称 ES6）是 JavaScript 语言的下一代标准，已经在 2015 年 6 月正式发布了。它的目标，是使得 JavaScript 语言可以用来编写复杂的大型应用程序，成为企业级开发语言。
### 1.3 什么是 ECMA-262
Ecma 国际制定了许多标准，而 ECMA-262 只是其中的一个，所有标准列表查看
[详细地址](http://www.ecma-international.org/publications/standards/Standard.htm)
### 1.4.ECMA-262 历史
#### ECMA-262（ECMAScript）[历史版本查看网址](http://www.ecma-international.org/publications/standards/Ecma-262-arch.htm)

| 版本          |     年份      |                                              制定了语言的基本语法 |
| :------------ | :-----------: | ----------------------------------------------------------------: |
| 第 2 版       |    1998 年    |                                                          较小改动 |
| 第 3 版       |    1999 年    |                     引入正则、异常处理、格式化输出等。IE 开始支持 |
| 第 4 版       |    2007 年    |                                                  过于激进，未发布 |
| 第 5 版       |    2009 年    |        引入严格模式、JSON，扩展对象、数组、原型、字符串、日期方法 |
| ***第 6 版*** | ***2015 年*** | 模块化、面向对象语法、Promise头函数、let、const、数组解构赋值等等 |
| 第 7 版       |    2016 年    |                            幂运算符、数组扩展、Async/await 关键字 |
| 第 8 版       |    2017 年    |                                           Async/await、字符串扩展 |
| 第 9 版       |    2018 年    |                                            对象解构赋值、正则扩展 |
| 第 10 版      |    2019 年    |                                                扩展对象、数组方法 |
| 第 11 版      |    2020 年    |      动态imports、import.meta、export加强、空值合并运算符、BigInt |
### 1.5ES6 兼容性 
[兼容性详情](http://kangax.github.io/compat-table/es6/)

## 2.ECMASript 6 新特性

### 2.1.1 let关键字

   let 关键字用来声明变量，使用 let 声明的变量有几个特点
   1. 不允许重复声明
   2. 块级作用域
   3. 不存在变量提升
   4. 不影响作用域链
   ***以后使用 let 就对了***

### 2.1.2 const 关键字
   const 关键字用来声明常量，const 声明有以下特点
   1. 声明必须赋初始值
   2. 常量名一般为大写
   3. 不允许重复声明
   4. 值不允许修改
   5. 块级作用域
### 2.1.3变量的解构赋值
      **注意：频繁使用对象方法、数组元素，就可以使用解构赋值形式**
     ```javascript
      //数组的解构赋值
      const arr = ['张学友', '刘德华', '黎明', '郭富城'];
      let [zhang, liu, li, guo] = arr;

      //对象的结构赋值
       const zhao = {
             name: '赵本山',
             age: '不详',
             xiaopin: function(){
                 console.log("我可以演小品");
             }
         };
      let {name,age,xiaopin} = zhao
      ``` 
### 2.1.4 模板字符串
   模板字符串（template string）是增强版的字符串，用反引号（`）标识
   特点：
   1. 字符串中可以出现换行符
   2. 可以使用 ${变量} 形式输出变量
   
   ```javascript
   //演示
   let  str= `测试`
   let model = `
   <html>
      <head></head>
      <body>
         <h1>${str}</h1>
      </body>
   </html>`
   ```

### 2.1.5简化对象写法
   ES6 允许在大括号里面，直接写入变量和函数，作为对象的属性和方法。这
样的书写更加简洁。
   ```javascript
      let name = 'es6+'
      let advantage = '新特性'
      let improve = function(){
         console.log('不断进步')
      }

   let intor={
      name:name,
      advantage:advantage,
      improve:improve，
      change(){
         console.log('change')
      }
   }
   ```

### 2.1.6 箭头函数
   ES6 允许使用 ()=>{}  定义函数
##### 基本语法
   ```javascript
      (param1,param2,..)=>{elements}
      let func = (arg1, arg2, ...argN) => expression

      // 当只有一个参数时，圆括号是可选的：
      (param) => { elements }
       param => { elements }

      // 没有参数的函数应该写成一对圆括号。
      () => { elements }

      //简化书写    
      let double = n => n * 2;
      // 差不多等同于：let double = function(n) { return n * 2 }

      //rest参数
     let rest = (param1,param2,...args)=>{
         console.log(args)
      }
      rest(1,2,3,4,5,6)
   ```
##### 箭头函数没有"this"
    箭头函数不能作为构造函数实例化
   this 是静态的. this 始终指向函数声明时所在作用域下的 this 的值
   ```
    'use strict';
   var obj = {
     a: 10
   };
   
   Object.defineProperty(obj, "b", {
     get: () => {
       console.log(this.a, typeof this.a, this);
       return this.a+10;
      // 代表全局对象 'Window', 因此 'this.a' 返回 'undefined'
     }
   });
   
   obj.b; // undefined   "undefined"   Window {postMessage: ƒ, blur: ƒ,    focus: ƒ, close: ƒ, frames: Window, …}
   ```
### 2.1.7 rest参数
   
   **注意：rest 参数非常适合不定个数参数函数的场境**
   ```javascript
      
   //作用与 arguments 类似
   
   function add(...args){
    console.log(args);
   }
   add(1,2,3,4,5);
   /**
   * rest 参数必须是最后一个形参
   */
   function minus(a,b,...args){
    console.log(a,b,args);
   }
   minus(100,1,2,3,4,5,19)
   ```
#### Spread语法
   Spread 语法 它看起来和 rest 参数很像，也使用 ...，但是二者的用途完全相反。
   ```javascript
      //以Math.max
      let arr1 = [1,4,9]
      let arr2 = [2,6,10]
      console.log(Math.max(...arr1))//--9  spread 语法把数组转换为参数列表
      //可以传递多个迭代对象
      console.log(Math.max(...arr1,...arr2))//--  10
      //结合常规之
      console.log(Math.max(...arr1,20,...arr2),-10)//-- 20

      //使用 spread 语法将字符串转换为字符数组：
      let str = 'hello'
      console.log([...str])   // h,e,l,l,o
   ```
### 2.1.8 Symbol
   ES6 引入了一种新的原始数据类型 Symbol，表示独一无二的值。它是JavaScript 语言的第七种数据类型，是一种类似于字符串的数据类型。
   **注: 遇到唯一性的场景时要想到 Symbol**
##### 2.1.8.1Symbol的基本使用
   -- Symbol 值通过Symbol函数生成。这就是说，对象的属性名现在可以有两种类型，一种是原来就有的字符串，另一种就是新增的 Symbol 类型。凡是属性名属于 Symbol 类型，就都是独一无二的，可以保证不会与其他属性名产生冲突。

   -- Symbol 值不能与其他数据进行运算
   --Symbol 定义 的 对象属 性 不能 使 用 for…in 循 环遍 历 ，但 是可 以 使用Reflect.ownKeys 来获取对象的所有键名
   ```javascript
   let s = Symbol()
   typeof s
   // "symbol"
   /*
   注意，Symbol函数前不能使用new命令，否则会报错。这是因为生成的 Symbol 是一个原始类型的值，不是对象。也就是说，由于 Symbol 值不是对象，所以不能添加属性。基本上，它是一种类似于字符串的数据类型。
   */
   ```
   ```javascript
  // Symbol函数可以接受一个字符串作为参数，表示对 Symbol 实例的描述，主要是为了在控制台显示，或者转为字符串时，比较容易区分。
   let s1 = Symbol('foo');
   let s2 = Symbol('bar');

   s1 // Symbol(foo) 
   s2 // Symbol(bar)

   s1.toString() // "Symbol(foo)"
   s2.toString() // "Symbol(bar)"
   ```
#### 2.1.8.2.Symbol 内置值
   除了定义自己使用的 Symbol 值以外，ES6 还提供了 11 个内置的 Symbol 值，指向语言内部使用的方法。

   **Symbol.hasInstance**
   对象的Symbol.hasInstance属性，指向一个内部方法。当其他对象使用
   instanceof运算符，判断是否为该对象的实例时，会调用这个方法。比如，o
   instanceof Person在语言内部,实际调用的是 o [Symbol.hasInstance (Person)
   ```javascript

   class Person {
            static[Symbol.hasInstance](param) {
                console.log(param);
                console.log("我被用来检测类型了");
                return false;
            }
        }

        let o = {};
        o instanceof Person;    //false
   /*
   上面代码中，Person是一个类，Person会返回一个实例。该实例的Symbol.
   hasInstance方法，会在进行instanceof运算时自动调用，判断左侧的运算子是为
   Person的实例。*/

        const arr = [1, 2, 3];
        const arr2 = [4, 5, 6];
        arr2[Symbol.isConcatSpreadable] = false;
        console.log(arr.concat(arr2));
   ```
   **Symbol.isConcatSpreadable**
   对象的Symbol.isConcatSpreadable属性等于一个布尔值，表示该对象用于Array. prototype.concat()时，是否可以展开。
   ```javascript
         const arr = [1, 2, 3];
        const arr2 = [4, 5, 6];
        arr2[Symbol.isConcatSpreadable] = false;
        console.log(arr.concat(arr2));    //[1, 2, 3, [4,5,6]]
   ```
| Syntax                    | Description                                                                                                          |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Symbol.hasInstance        | 当其他对象使用 instanceof 运算符，判断是否为该对象的实例时，会调用这个方法                                           |
| Symbol.isConcatSpreadable | 对象的 Symbol.isConcatSpreadable 属性等于的是一个布尔值该对象用于 Array.prototype.concat()时，是否可以展开。         |
| Symbol.species            | 创建衍生对象时，会使用该属性Symbol.match 当执行 str.match(myObject) 时如果该属性存在，会调用它，返回该方法的返回值。 |
| Symbol.replace            | 当该对象被 str.replace(myObject)方法调用时，会返回该方法的返回值。                                                   |
| Symbol.search             | 当该对象被 str.search (myObject)方法调用时，会返回该方法的返回值。                                                   |
| Symbol.split              | 当该对象被 str.split(myObject)方法调用时，会返回该方法的返回值。                                                     |
| Symbol.iterator           | 对象进行 for...of 循环时，会调用 Symbol.iterator 方法，返回该对象的默认遍历器                                        |
| Symbol.toPrimitive        | 该对象被转为原始类型的值时，会调用这个方法，返回该对象对应的原始类型值。                                             |
| Symbol. toStringTag       | 在该对象上面调用 toString 方法时，返回该方法的返回值                                                                 |
| Symbol. unscopables       | 该对象指定了使用 with 关键字时，哪些属性会被 with环境排除。                                                          |


### 2.1.9迭代器
遍历器（Iterator）就是一种机制。它是一种接口，为各种不同的数据结构提
供统一的访问机制。任何数据结构只要部署 Iterator 接口，就可以完成遍历操作。

 1. ES6 创造了一种新的遍历命令 for...of 循环，Iterator 接口主要供 for..of消费
 2. 原生具备 iterator 接口的数据(可用 for of 遍历)
   a) Array
   b) Arguments
   c) Set
   d) Map
   e) String
   f) TypedArray
   g) NodeList
3. 工作原理
a) 创建一个指针对象，指向当前数据结构的起始位置
b) 第一次调用对象的 next 方法，指针自动指向数据结构的第一个成员
c) 接下来不断调用 next 方法，指针一直往后移动，直到指向最后一个成员
d) 每调用 next 方法返回一个包含 value 和 done 属性的对象

**注: 需要自定义遍历数据的时候，要想到迭代器**

### 2.2.0 promise
promise是解决异步编程的**新解决方案**
语法上 Promise 是一个构造函数，用来封装异步操作并可以获取其成功或失败的结果。
1) Promise 构造函数: Promise (excutor) {}
2) Promise.prototype.then 方法
3) Promise.prototype.catch 方法

```javascript
   const p = new Promise((fulfill,reject)=>{
         let data = "数据"
         // fulfill(data)  调用第一个参数为成功
         // reject(data)  调用第二个参数为失败
         // PromiseResult=调用函数的形参

   })
   p.then(fulfilled=>{
         console.log(fulfilled)
   })catch(rejected=>{
         console.error(rejected)
   })

```

### 2.2.1 Set
ES6 提供了新的数据结构 Set（集合）。它类似于数组，但成员的值都是唯
一的，集合实现了 iterator 接口，所以可以使用『扩展运算符』和『for…of…』进
行遍历，集合的属性和方法：
1) size 返回集合的元素个数
2) add 增加一个新元素，返回当前集合
3) delete 删除元素，返回 boolean 值
4) has 检测集合中是否包含某个元素，返回 boolean 值
5) clear 清空集合，返回 undefined

```javascript
   //创建一个空集合
   let s = new Set()
   let s2 = new Set(['1', '2', '3', '4'])
   //集合属性与方法
   //返回集合的元素个数
   console.log(s1.size);
   //添加新元素
   console.log(s1.add(4));
   //删除元素
   console.log(s1.delete(1));
   //检测是否存在某个值
   console.log(s1.has(2));
   //清空集合
   console.log(s1.clear());
   
        for (const s of s2) {
            console.log(s);
        }
```

### 2.2.2 Map
ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合。但是“键”
的范围不限于字符串，各种类型的值（包括对象）都可以当作键。Map 也实现了
iterator 接口，所以可以使用『扩展运算符』和『for…of…』进行遍历。Map 的属
性和方法
1) size 返回 Map 的元素个数
2) set 增加一个新元素，返回当前 Map
3) delete 删除元素，返回 boolean 值
4) get 返回键名对象的键值
5) has 检测 Map 中是否包含某个元素，返回 boolean 值
6) clear 清空集合，返回 **undefined**

```javascript
  //声明一个Map
        let m = new Map()
        m.set('name', 'LongYa_Shadow')
        m.set('nickname', 'shadow')
        let key = {
            school: 'ATGUIGU'
        }
        m.set(key, ['北京', '深圳', '上海'])
        console.log(m); //查看Map对象
        console.log(m.get('nickname')); //get 返回键名对象的键值
        console.log(m.has(key)); //has 检测 Map 中是否包含某个元素，返回 boolean 值
        console.log(m.delete('name')); //delete 删除元素，返回 boolean 值
        console.log(m.size); //size 返回 Map 的元素个数
        console.log(m.clear()); //clear 清空集合，返回 **undefined**
```

### 2.2.3 Class 类
 ES6 提供了更接近传统语言的写法，引入了 Class（类）这个概念，作为对
象的模板。通过 class 关键字，可以定义类。基本上，ES6 的 class 可以看作只是
一个语法糖，它的绝大部分功能，ES5 都可以做到，新的 class 写法只是让对象
原型的写法更加清晰、更像面向对象编程的语法而已。
1) class 声明类
2) constructor 定义构造函数初始化

``` javascript
  // 生成实例对象的传统方法是通过构造函数
        function Point(x, y) {
            this.x = x
            this.y = y
        }
        //添加方法
        Point.prototype.toString = function() {
                return ('(' + this.x + ', ' + this.y + ')')
            }
            // 实例化对象
        let p = new Point(1, 2)
        console.log(p.toString());
        //class语法
        class Points {
            // 构造方法，而this关键字则代表实例对象
            constructor(x, y) {
                    this.x = x
                    this.y = y
                }
                //定义其他方法直接加进去，不需用括号
            toString() {
                return ('(' + this.x + ', ' + this.y + ')')
            }
        }
        let p2 = new Points(1, 2)
        console.log(p2.toString() == p.toString());
```
3) static 定义静态方法和属性
```javascript
    //传统方法
        function Point(x, y) {
            this.x = x
            this.y = y
        }
        //直接添加属于函数对象
        Point.x = 1
        Point.y = 2
        Point.toString = function() {
                return ('(' + this.x + ', ' + this.y + ')')
            }
            // 添加到原型上，实例对象可根据原型链找到
        Point.prototype.change = function() {
            return ("change");
        }
        let point = new Point()
        console.log(point);
        console.log(point.change());
        //class语法
        class Points {
            //静态属性
            static x = 1
            static y = 2
        }
        let points = new Points()
        console.log(points.x); //取不到
        console.log(Points.x); //静态属性通过类调用
```
4) extends 继承父类
5) super 调用父级构造方法
6) 父类方法可以重写
```javascript
  class Phone {
            //构造方法
            constructor(brand, price) {
                    this.brand = brand;
                    this.price = price;
                }
                //父类的成员属性
            call() {
                console.log("我可以打电话!!");
            }
        }

        class SmartPhone extends Phone {
            //构造方法
            constructor(brand, price, color, size) {
                super(brand, price); // Phone.call(this, brand, price)
                this.color = color;
                this.size = size;
            }

            photo() {
                console.log("拍照");
            }

            playGame() {
                console.log("玩游戏");
            }

            call() {
                console.log('我可以进行视频通话');
            }
        }

        const xiaomi = new SmartPhone('小米', 799, '黑色', '4.7inch');
        // console.log(xiaomi);
        xiaomi.call();
        xiaomi.photo();
        xiaomi.playGame();
```
7) get与set
```javascript
 class Phone {
            get price() {
                return "价格属性被读取了"
            }

            set price(value) {
                console.log("价格属性被修改了")
            }
        }

        // 实例化对象
        let phone = new Phone()
        console.log(phone.price);
        phone.price = "2200"
```

### 2.2.3 数值扩展
   1. Number.EPSILON 是 JavaScript 表示的最小精度
        //EPSILON 属性的值接近于 2.2204460492503130808472633361816E-16
   2. 二进制和八进制
   `let b = 0b1010;`二进制转为十进制 10
   `let o = 0o777;`八进制转为十进制 511
   `let x = 0xff;`十六进制转为十进制 255
   3. Number.isFinite  检测一个数值是否为有限数
   ```javascript
      console.log(Number.isFinite(100)); //true
      console.log(Number.isFinite(100/0));//false  100/0=Infinity
      console.log(Number.isFinite(Infinity));//false
   ```
  4. Number.isNaN 检测一个数值是否为 NaN 
      `console.log(Number.isNaN(123)); `   

 
   5. Number.parseInt Number.parseFloat字符串转整数
       ` console.log(Number.parseInt('5211314love'));`
         `console.log(Number.parseFloat('3.1415926神奇'));`

   6. Number.isInteger 判断一个数是否为整数
       ` console.log(Number.isInteger(5));
        console.log(Number.isInteger(2.5));`

    7. Math.trunc 将数字的小数部分抹掉  
      `  console.log(Math.trunc(3.5));`

    8. Math.sign 判断一个数到底为正数 负数 还是零
   ```javascript
    console.log(Math.sign(100));    //1
        console.log(Math.sign(0));  //0
        console.log(Math.sign(-20000));//-1
   ```
### 2.2.4 对象扩展
ES6新增了一些Object对象的方法 
1) Object.is 比较两个值是否严格相等，与『===』行为基本一致（+0 与 NaN） 
2) Object.assign 对象的合并，将源对象的所有可枚举属性，复制到目标对象 
3) __proto__、setPrototypeOf、 setPrototypeOf可以直接设置对象的原型


### 2.2.6 模块化
模块化是指将一个大的程序文件，拆分成许多小的文件，**然后将小文件组合起**
#### 模块化的优势有以下几点： 
1) 防止命名冲突 
2) 代码复用 
3) 高维护性
#### 模块化基本语法
模块功能主要由两个命令构成：export和import。 
1. export命令用于规定模块的对外接口 
2. import命令用于输入其他模块提供的功
```javascript
// 分别为单个js文件
{
    //单个暴露
    export let name = "longya"
} {

    //统一暴露
    let name = "longya"
    function study() {
        console.log("--");
    }
    export { name, study }
}
{
    //默认暴露
    export default {
        shool: "文理",
        change() {
            console.log("牛马");
        }
    }
}

// 模块引入
import * as m1 from "./文件名.js"
import * as m2 from "./文件名.js"
import * as m3 from "./文件名.js"

//简便形式 针对默认暴露 
import m4 from "./文件.js";

```
## 3 ECMASript 6 新特性
### 3.1 Array.prototype.includes 
Includes 方法用来检测数组中是否包含某个元素，返回布尔类型
在ES7中引入指数运算符「**」，用来实现幂运算，功能与Math.pow结果相同
```javascript
//includes indexOf
        let masterpiece = ['西游记', '红楼梦', '三国演义', '水浒传']
            //判断
        console.log(masterpiece.includes('西游记')); //true
        console.log(masterpiece.includes('金梅瓶')); //false

        //**  平方
        console.log(2 ** 10);
         console.log(Math.pow(2, 10));

```

## 4.ECMASript 8  新特性
### 4.1 async 和 await
async和await两种语法结合可以让异步代码像同步代码一样 
### 4.1.1. async函数 
1. async函数的返回值为promise对象， 
2. promise对象的结果由async函数执行的返回值决定 
### 4.1.2. await表达式 
1. await必须写在async函数中  
2. await右侧的表达式一般为promise对象 
3. await返回的是promise成功的值 
4. await的promise失败了, 就会抛出异常, 需要通过try...catch捕获处

## 5 ECMASript 9  新特性
### 5.1 Rest/Spread属性
Rest 参数与 spread 扩展运算符在 ES6 中已经引入，不过 ES6 中只针对于数组，
在ES9中为对象提供了像数组一样的rest参数和扩展运算符
```javascript
//对象合并
        const skillOne = {
            q: '天音波'
        }

        const skillTwo = {
            w: '金钟罩'
        }

        const skillThree = {
            e: '天雷破'
        }
        const skillFour = {
            r: '猛龙摆尾'
        }

        const mangseng = {
            ...skillOne,
            ...skillTwo,
            ...skillThree,
            ...skillFour
        };
        console.log(mangseng);
```

### 5.2 正则表达式命名捕获分组
```javascript
let str = '<a href="javascript:void(0);">空标签</a>'
        let reg = /<a href="(.*)">(.*)<\/a>/
        let result = reg.exec(str)

        console.log(result[0]);
        console.log(result[1]);//javascript:void(0);
        console.log(result[2]);//空标签

        // -----------------------------
        // 给组加别名 加到groups对象中
        let str = '<a href="javascript:void(0);">空标签</a>'
        let reg = /<a href="(?<url>.*)">(?<text>.*)<\/a>/
        let result = reg.exec(str)
        console.log(result);
        console.log(result.groups.url); //javascript:void(0);
        console.log(result.groups.text); //空标签
```
### 5.3 正则表达式反向断言
ES9支持反向断言，通过对匹配结果前面的内容进行判断，对匹配进行筛
```javascript
    //声明字符串
        let str = "JSON12345正则表达式54321反向断言"
            //  /d 0-9数字  ?=判断  正向断言
            // let reg = /\d+(?=反)/
            // let result = reg.exec(str)
            //反向断言
        let reg = /(?<=式)\d+/
        let result = reg.exec(str)
        console.log(result);

```
### 5.4 正则表达式dotAll模式
正则表达式中点.匹配除回车外的任何单字符，标记『s』改变这种行为，允许行
终止符出现
```javascript
        //dot . 元字符  除换行符以外的任意字符
        //\s单个空白字符(换行符而算)
        let str = `
        <ul> 
          <li> 
              <a>肖生克的救赎</a> 
              <p>上映日期: 1994-09-10</p> 
          </li> 
          <li> 
              <a>阿甘正传</a> 
              <p>上映日期: 1994-07-06</p> 
          </li> 
      </ul>
        `
            //声明正则
            // const reg = /<li>\s+<a>(.*?)<\/a>\s+<p>(.*?)<\/p>\s+<\/li>/
        const reg = /<li>.*?<a>(.*?)<\/a>.*?<p>(.*?)<\/p>.*?<\/li>/gs

        //执行匹配
        let data = []
        let result
        while (result = reg.exec(str)) {
            console.log(result);
            data.push({
                title: result[1],
                times: result[2]
            })
        }
        console.log(data);

```

## 6 ECMASript 10  新特性
### 6.1 Object.fromEntries 
Object.fromEntries() 方法接收一个键值对的列表参数，并返回一个带有这些键值对的新对象。这个迭代参数应该是一个能够实现@@iterator方法的的对象，返回一个迭代器对象。它生成一个具有两个元素的类数组的对象，第一个元素是将用作属性键的值，第二个元素是与该属性键关联的值。

Object.fromEntries() 执行与 Object.entries 互逆的操作。
```javascript
    // 二维叔祖 转对象
        // let result = Object.fromEntries([
        //     ['name', 'LongYa_shadow'],
        //     ['nickanme', 'shadow']
        // ])

        let m = new Map()
        m.set('name', 'LongYa_Shadow')
        let result = Object.fromEntries(m)
        console.log(result);

        //Object.Entries  对象转二维数组
        let arr = Object.entries({
            name: "LongYa_Shadow"
        })
        console.log(arr);
```
### 6.2 trimStart和trimEnd
```javascript
   let str = '    iloveyou   '
        console.log(str.trim());
        console.log(str.trimStart());
        console.log(str.trimEnd());
```

### 6.3 Symbol.prototype.description
```javascript
// 创建Symbol
let s = new Symbol("symbol")
console.log(s.description);//symbol

```

## 7 ECMASript 11  新特性
### 7.1 类的私有属性
```javascript
     class Person {
            name;
            age;
            weight;
            // 构造方法==set
            constructor(name, age, weight) {
                this.name = name
                this.age = age
                this.weight = weight
            }
            intor() {
                console.log(this.name);
                console.log(this.age);
                console.log(this.weight);
            }
        }
        let girl = new Person('李师师', 27, "45kg")
        console.log(girl);
        girl.intor() 
```

### 7.2  String.prototype.matchAll
```javascript
 //\s单个空白字符(换行符而算)
        let str = `
        <ul> 
          <li> 
              <a>肖生克的救赎</a> 
              <p>上映日期: 1994-09-10</p> 
          </li> 
          <li> 
              <a>阿甘正传</a> 
              <p>上映日期: 1994-07-06</p> 
          </li> 
      </ul>
        `
        const reg = /<li>.*?<a>(.*?)<\/a>.*?<p>(.*?)<\/p>/gs
    let result  = str.matchAll(reg)
    console.log(result);
   for(let v of result)  {
       console.log(v);
   }
   let arr = [...result]
   console.log(arr);
```

<!-- ### 7.3可选链操作符
```javascript
// ？.
        function main(config) {
            // let dbHost = config && config.db && config.db.host
            const dbHost = config?.db?.host;
            console.log(dbHost);
        }

        main({
            db: {
                host: '192.168.1.1',
                username: 'root'
            },
            cache: {
                host: '192.168.1.1',
                username: 'admin'
            }

        })
``` -->

### 7.3 动态import
根据需求加载模块 
import('文件名')返回的是一个Promise

点击加载模块
```html
    <button id="btn">点击</button>
    <script src="./js/app.js"></script>
```
app.js
```javascript
    let btn = document.getElementById("btn")
btn.addEventListener('click', () => {
    import ('./hello.js').then(module => {
        module.hello()
    })
})
```
js模块
```javascript
export function hello() {
    console.log("hello");
}
```

### 7.4 BigInt
igInt 是一种内置对象，它提供了一种方法来表示大于 253 - 1 的整数。这原本是 Javascript中可以用 Number 表示的最大数字。BigInt 可以表示任意大的整数。
```javascript
 //大整形
        // let n = 521n;
        // console.log(n, typeof(n));

        //函数
        // let n = 123;
        // console.log(BigInt(n));
        // console.log(BigInt(1.2));

        //大数值运算
        let max = Number.MAX_SAFE_INTEGER;
        console.log(max);
        console.log(max + 1);
        console.log(max + 2);
        //转换类型才能运算
        console.log(BigInt(max))
        console.log(BigInt(max) + BigInt(1))
        console.log(BigInt(max) + BigInt(2))
```

### 7.5 globalThis
全局属性 globalThis 包含全局的 this 值，类似于全局对象（global object）
` console.log(globalThis);//window`