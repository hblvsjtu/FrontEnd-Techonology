# FET

## 作者：冰红茶  
    
------    
    
平常在生活中或者工作中不断的学习前端知识，记录和分享吾之所见吾之所悟^_ ^
- [FET](#fet)
  - [作者：冰红茶](#作者冰红茶)
  - [〇、基础知识篇](#〇基础知识篇)
    - [0.1 this与闭包](#01-this与闭包)
      - [1) this的优先级](#1-this的优先级)
      - [2) 按顺序打印0～9](#2-按顺序打印09)
      - [3) 变量提升和暂时性死区](#3-变量提升和暂时性死区)
      - [4) 闭包](#4-闭包)
      - [5) 内存泄漏的几种情况](#5-内存泄漏的几种情况)
  - [一、类型判断篇](#一类型判断篇)
    - [1.1 基本数字类型](#11-基本数字类型)
      - [1) null](#1-null)
      - [2) NaN](#2-nan)
      - [3) undefined](#3-undefined)
      - [4) number](#4-number)
      - [5) boolean](#5-boolean)
    - [1.2 对象类型系统](#12-对象类型系统)
      - [1) object](#1-object)
      - [2) 函数](#2-函数)
      - [3) 正则表达式](#3-正则表达式)
      - [4) 日期](#4-日期)
      - [5) 数组](#5-数组)
      - [6) 全类型判断](#6-全类型判断)
    - [1.3 平台](#13-平台)
      - [1) window](#1-window)
      - [2）浏览器](#2浏览器)
  - [二、常用方法篇](#二常用方法篇)
    - [2.1 拷贝](#21-拷贝)
      - [1) 数组浅拷贝](#1-数组浅拷贝)
      - [2) 数组深拷贝](#2-数组深拷贝)
    - [2.2 类数组判断与转化](#22-类数组判断与转化)
      - [1) 判断](#1-判断)
      - [2) slice的内部实现](#2-slice的内部实现)
      - [3) 转化](#3-转化)
    - [2.4 数组乱序](#24-数组乱序)
    - [2.8 ajax封装](#28-ajax封装)
      - [1) 功能](#1-功能)
    - [2.9 String.format](#29-stringformat)
      - [1) 功能](#1-功能-1)
      - [2) 一个更加简介的办法：利用replace()](#2-一个更加简介的办法利用replace)
    - [2.10 String.thousandSplit](#210-stringthousandsplit)
      - [1) 功能](#1-功能-2)
      - [2) 实现](#2-实现)
  - [三、原理实现篇](#三原理实现篇)
    - [3.1 call/apply/bind](#31-callapplybind)
      - [1) call](#1-call)
      - [2) apply](#2-apply)
      - [3) bind](#3-bind)
    - [3.2 Deferred和Promise](#32-deferred和promise)
      - [1) promise/A规范](#1-promisea规范)
      - [2) Deferred/promise](#2-deferredpromise)
      - [2) Promise(第一次自己写的)](#2-promise第一次自己写的)
      - [3) Promise(看了别人代码后自己写的)](#3-promise看了别人代码后自己写的)
    - [3.4 观察者模式](#34-观察者模式)
      - [1) 要点](#1-要点)
      - [2) 代码](#2-代码)
    - [3.5 防抖动和截流](#35-防抖动和截流)
      - [1) 相同点](#1-相同点)
      - [2) 不同点](#2-不同点)
      - [3) 防抖动](#3-防抖动)
      - [4) 截流/频率控制](#4-截流频率控制)
      - [5) 防抖动和截流合并](#5-防抖动和截流合并)
    - [3.6 类的继承](#36-类的继承)
      - [1) 属性拷贝](#1-属性拷贝)
      - [2) 原型式继承](#2-原型式继承)
      - [3) 原型链继承](#3-原型链继承)
      - [4) 构造函数继承](#4-构造函数继承)
      - [5) 组合继承](#5-组合继承)
      - [6) 组合继承优化1](#6-组合继承优化1)
      - [7) 组合继承优化2](#7-组合继承优化2)
    - [3.7 new](#37-new)
      - [1) 要点](#1-要点-1)
    - [3.8 Object.create()](#38-objectcreate)
      - [1) 参数](#1-参数)
    - [3.9 Object.keys/Object.values/Object.entries](#39-objectkeysobjectvaluesobjectentries)
      - [1) Object.keys](#1-objectkeys)
      - [2) Object.values](#2-objectvalues)
      - [2) Object.entrie](#2-objectentrie)
    - [3.10 setTimeout 与 setInterval](#310-settimeout-与-setinterval)
      - [1) 最短间隔时间](#1-最短间隔时间)
    - [3.11 跨域](#311-跨域)
      - [1) 通过document.domain跨域](#1-通过documentdomain跨域)
      - [2) 通过location.hash跨域](#2-通过locationhash跨域)
      - [3) 通过postMessage](#3-通过postmessage)
      - [4) Jsonp](#4-jsonp)
      - [5) Access-Control-Allow-Origin](#5-access-control-allow-origin)
    - [3.12 函数柯里化](#312-函数柯里化)
      - [1) 定义](#1-定义)
      - [2) 两段不定参数版本](#2-两段不定参数版本)
      - [3) 不定段不定参数版本](#3-不定段不定参数版本)
    - [3.13 高阶函数](#313-高阶函数)
      - [1) 定义](#1-定义-1)
      - [2) 实现一个map函数](#2-实现一个map函数)
      - [3) 实现一个forEach函数](#3-实现一个foreach函数)
      - [4) 实现一个reduce函数](#4-实现一个reduce函数)
      - [5) 实现一个filter函数](#5-实现一个filter函数)
    - [3.14 迭代器](#314-迭代器)
      - [1) 定义](#1-定义-2)
    - [3.15 instanceof](#315-instanceof)
      - [1) 定义](#1-定义-3)
  - [四、正则表达式](#四正则表达式)
    - [4.1 断言](#41-断言)
      - [1) 定义](#1-定义-4)
      - [2) 类型](#2-类型)
    - [4.2 反向引用](#42-反向引用)
      - [1) 定义](#1-定义-5)
      - [2) 要点](#2-要点)
    - [4.3 非贪婪](#43-非贪婪)
      - [1) 定义](#1-定义-6)
    - [4.4 电话号码/身份证/网址/邮箱](#44-电话号码身份证网址邮箱)
      - [1) QQ号码](#1-qq号码)
      - [2) 电话号码](#2-电话号码)
      - [3) 身份证](#3-身份证)
      - [3) 网址](#3-网址)
      - [4) 邮箱](#4-邮箱)
  - [五、js和html效果篇](#五js和html效果篇)
    - [5.1 获取元素样式/位置/尺寸](#51-获取元素样式位置尺寸)
      - [1) 样式](#1-样式)
      - [2) 位置](#2-位置)
    - [5.2 拖拽](#52-拖拽)
      - [1) 行内元素](#1-行内元素)
    - [5.3 图片懒加载](#53-图片懒加载)
      - [1) 行内元素](#1-行内元素-1)
    - [5.4 轮播](#54-轮播)
      - [1) 行内元素](#1-行内元素-2)
    - [5.5 滑动](#55-滑动)
      - [1) 行内元素](#1-行内元素-3)
    - [5.6 级联](#56-级联)
      - [1) 行内元素](#1-行内元素-4)
    - [5.7 图片剪裁](#57-图片剪裁)
      - [1) 行内元素](#1-行内元素-5)
    - [5.8 图片压缩](#58-图片压缩)
      - [1) 行内元素](#1-行内元素-6)
    - [5.9 Tab](#59-tab)
      - [1) 行内元素](#1-行内元素-7)
  - [六、CSS效果篇](#六css效果篇)
    - [6.1 水平居中](#61-水平居中)
      - [1) 行内元素](#1-行内元素-8)
      - [2) 块级元素](#2-块级元素)
    - [6.2 垂直居中](#62-垂直居中)
      - [1) 行内元素](#1-行内元素-9)
      - [2) 块级元素](#2-块级元素-1)
    - [6.3 水平垂直居中](#63-水平垂直居中)
      - [1) 绝对定位auto方案](#1-绝对定位auto方案)
      - [2) 绝对定位translate方案](#2-绝对定位translate方案)
      - [3) inline-block方案](#3-inline-block方案)
      - [4) table-cell方案](#4-table-cell方案)
    - [6.4 清除浮动](#64-清除浮动)
      - [1) 原因](#1-原因)
      - [2) 解决办法](#2-解决办法)
    - [6.5 幽灵空白节点](#65-幽灵空白节点)
      - [1) W3C规范](#1-w3c规范)
      - [2) 如何消除呢？](#2-如何消除呢)
    - [6.6 三列布局](#66-三列布局)
      - [1) 双飞翼布局](#1-双飞翼布局)
      - [2) 圣杯布局](#2-圣杯布局)
      - [3) 简单float布局](#3-简单float布局)
      - [4) 绝对float布局](#4-绝对float布局)
      - [5) 绝对布局](#5-绝对布局)
    - [6.7 弹性布局](#67-弹性布局)
      - [1) 容器](#1-容器)
      - [2) 主轴方向：flex-direction:](#2-主轴方向flex-direction)
      - [3) 换行显示：flex-wrap](#3-换行显示flex-wrap)
      - [4) flex-flow](#4-flex-flow)
      - [5) 定义项目在主轴上的对齐方式：justify-content](#5-定义项目在主轴上的对齐方式justify-content)
      - [6) 定义项目在交叉轴上的对齐方式：align-items](#6-定义项目在交叉轴上的对齐方式align-items)
      - [7) 项目中的属性](#7-项目中的属性)
      - [7) align-self](#7-align-self)
      - [8) flex-grow和flex-shrink相关计算公式](#8-flex-grow和flex-shrink相关计算公式)
      - [9) 手写一个圣杯布局](#9-手写一个圣杯布局)
    - [6.8 响应式布局](#68-响应式布局)
      - [1) null](#1-null-1)
    - [6.9 变形动画](#69-变形动画)
      - [1) 二维动画](#1-二维动画)
      - [2) 三维动画](#2-三维动画)
    - [6.10 补间动画](#610-补间动画)
      - [1) null](#1-null-2)
  - [九、浏览器篇](#九浏览器篇)
    - [9.3 defer和async的区别](#93-defer和async的区别)
      - [1) 相同点](#1-相同点-1)
      - [2) 不同点](#2-不同点-1)
    - [9.5 浏览器性能和计时器](#95-浏览器性能和计时器)
      - [1) 高消耗的样式](#1-高消耗的样式)
      - [2) 减少重排Reflow的经验](#2-减少重排reflow的经验)
      - [3) 优化动画性能](#3-优化动画性能)
    - [10.0 事件循环](#100-事件循环)
      - [1) 主线程](#1-主线程)
      - [2) 任务队列(Macrotasks)](#2-任务队列macrotasks)
      - [3) 微任务队列(Microtasks)](#3-微任务队列microtasks)

        
------      
## 〇、基础知识篇
### 0.1 this与闭包

#### 1) this的优先级
> - 箭头函数
> - new
> - call,apply,bind
> - 对象的函数属性调用
> - 全局window的函数属性调用

#### 2) 按顺序打印0～9
> - 1秒后同时打印0～9 关键点在于创造n个不同的独立作用域
```js
    // 闭包
    for (var i = 0; i < 10; i++) {
        (function(j) {
            setTimeout(function() {console.log(j)}, 1000);
        })(i);
    }

    // let
    for (let i = 0; i < 10; i++) {
        setTimeout(function() {console.log(a)}, 1000);
    }
```

> - 每秒按顺序打印0～9
```js
        // setInterval法
        i = 0;
        timer = setInterval(function() {
            console.log(i++);
            if(i === 10) clearInterval(timer);
        }, 1000);

        // promise法
        function getDelayPromise(i) {
            return new Promise(function (resolve, reject){
                setTimeout(function() {resolve(i)}, 1000);
            })
        };
        var delay = getDelayPromise(0);
        for (var i = 0; i < 10; i++) {
            delay = delay.then(function(res) {
                console.log(res);
                return getDelayPromise(res + 1);
            });
        };

        // await法
        function getDelayPromise(i) {
            return new Promise(function (resolve, reject){
                setTimeout(function() {resolve(i)}, 1000);
            })
        };

        (async function() {
            for (var i = 0; i < 10; i++) {
                console.log(await getDelayPromise(i));
            }
        })();
}
```

#### 3) 变量提升和暂时性死区
> - 这两个概念是相对而言的
> - js 是一种解释性的语言 分为``预编译阶段``和``执行阶段``，``执行阶段``中解释一行然后执行一行。在预编译过程为了提前预先配好内存，中会对函数中的var变量声明部分提前提升至函数的开始，并赋值为undefined，然后在执行过程中再重新赋值。这个过程成为``变量提升``。而``let``和``const``则不那么幸运，``预编译阶段``不会被【提升】，所以从函数开始到变量声明前被成为``暂时性死区``，访问的时候会报``referenceError``引用错误。
> - 函数的变量在预编译阶段被创建，在执行阶段被激活，在函数执行完毕后的下一个垃圾回收GC节点被回收，其上下文也会被销毁

#### 4) 闭包
> - 函数嵌套时，内部函数可访问了外部函数的作用域变量，哪怕内部函数是在全局环境下被调用
> - 一般来说是全局环境是不可访问函数内部的变量的，但是通过闭包，就可以实现对函数内部变量的访问，并且不会污染全局变量
> - 有个坏处，容易造成内存泄露，不用的时候需要把内部函数的引用置为null
> - 闭包只使用内部函数在第一次建立时候的作用域链

#### 5) 内存泄漏的几种情况
> - 闭包
> - 删除节点
> - 设置事件监听

## 一、类型判断篇
### 1.1 基本数字类型
 
#### 1) null
> - 直接跟v他自己比较即可
```js
                function isNull(o) {
                    return o === null;
                }
```
#### 2) NaN
> - 因为它连跟它自己比较都不相等，可以用此特性进行判断
```js           
                function isNaN(o) {
                    return o !== o;
                }
```

#### 3) undefined
> - undefined它并不是一个保留词，他是全局对象的一个属性，这说明什么呢？说明它有可能会被改写。到了ES5被改成只读了，但是在局部作用域中还是会被改写，虽然在最新的chrome 75.0.3770.142中我并没有发现改写-.-||
> - 为什么是void 0? 因为根据MDN的解释：The void operator evaluates the given expression and then returns undefined. 无论你给他赋什么的值，都会返回undefined，而0应该是最简单的喽
```js 
                function isUndefined(o) {
                    return o === void 0;
                }
```

#### 4) number
> - 采用鸭子辩型
> - 因为如果纯粹使用typeof的话会把包装类也识别成对象；
```js
                function isNumber(o) {
                    return '[object Number]' === {}.toString.call(o) && isFinite(o); 
                }
```

#### 5) boolean
> - 采用鸭子辩型
> - 因为如果纯粹使用typeof的话会把包装类也识别成对象；
```js
                function isboolean(o) {
                    return '[object Boolean]' === {}.toString.call(o); 
                }
```

### 1.2 对象类型系统

#### 1) object
> - 
```js
                function isObject(o) {
                    return '[object Object]' === {}.toString.call(o); 
                }
```

#### 2) 函数
> - 
```js   
                function isFunction(o) {
                    return '[object Function]' === {}.toString.call(o); 
                }
```

#### 3) 正则表达式
> - 
```js
                function isRegExp(o) {
                    return '[object RegExp]' === {}.toString.call(o); 
                }
```

#### 4) 日期
> - 
```js
                function isDate(o) {
                    return '[object Date]' === {}.toString.call(o); 
                }
```

#### 5) 数组
> - 
```js
                function isArray(o) {
                    return '[object Array]' === {}.toString.call(o); 
                }
```

#### 6) 全类型判断
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                function type(o) {
                    if(o === null) return "null";
                    else if(o !== o) return "NaN";
                    else if(o === void 0) return "undefined";
                    else {
                        let type = {}.toString.call(o).slice(8, -1);
                        return type ? type : '它不是基本类型'
                    }
                }
```

### 1.3 平台
        
#### 1) window
> - 需要区分不同的平台
> - IE6、7、8利用window == document为真 但是document == window为假的神奇特性
> - 标准浏览器及IE9,IE10等使用鸭子辩型的方法
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                // IE6、7、8
                function isWindow(obj) {
                    return obj == obj.document && obj.document != obj;
                }
                // 标准浏览器及IE9,IE10
                function isWindow(obj) {
                    return /^\[object (Window|DOMWindow|global)/.test({}.toString.call(obj));
                }
```

#### 2）浏览器
> - 判断浏览器类型
> - 利用navigator.userAgent来判断
> - 要把browsers数组里面的子项按照顺序来放，因为有时候userAgent里面会同时出现两种或以上的子项，当Safari出现的时候一般在userAgent的最后面，而"Chrome"次之，所以需要把他们放在前面先进行遍历
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                function myBrowser(){
                    var userAgent = navigator.userAgent; //取得浏览器的userAgent字符串
                    // 此处要把
                    let browsers = ["Safari", "Opera", "Firefox", "Chrome", "Edge", "compatible"];
                    let browser = '';
                    browsers.forEach(item => {
                        if(userAgent.indexOf(item) > -1)
                            browser = item;
                    })
                    if(browser === "compatible") {
                        if(browser =userAgent.match(/(?:MSIE\s*)\d{1,2}.0(?=\s*;)/)) {
                            browser = browser[0].replace('MS', '')
                        }
                    }
                    return browser;
                }             
```

------      
        
## 二、常用方法篇
### 2.1 拷贝

        
#### 1) 数组浅拷贝
> - Object.assign
> - 
#### 2) 数组深拷贝
> - 先对输入进行判断，是数组、对象还是其他
> - 然后如果是数组或者对象的时候进行遍历，子元素是数组或者对象的时候直接赋值，否则进行递归
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                let deepCopy = function(obj) {
                    let o;
                    let type = Object.prototype.toString.call(obj);
                    if(type === '[object Array]' || type === '[object Object]') {
                        o = type === '[object Array]' ? [] : {};
                        for(let key in obj) {
                            if(obj.hasOwnProperty(key)) {
                                if(typeof obj[key] === 'Object') {       
                                    o[key] = deepCopy(obj[key]);
                                }
                                else {
                                    o[key] = obj[key];
                                }
                            }
                        }
                    }
                    else {
                        o = obj;
                    }
                    return o;
                };
```

### 2.2 类数组判断与转化

        
#### 1) 判断
> - 是一个对象
> - 有length属性
> - length属性的值是一个非负有限整数
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                function isArrayLike(obj) {
                    return obj && (typeof obj === 'object') &&  (obj.length >= 0) &&  obj.length < 4294967296 && (obj.length === Math.floor(obj.length))
                }
```

#### 2) slice的内部实现
> - 返回一个数组
> - 循环赋值从0到length
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                //slice的内部实现
                Array.prototype.slice = function(start,end){  
                      var result = new Array();  
                      start = start || 0;  
                      end = end || this.length; //this指向调用的对象，当用了call后，能够改变this的指向，也就是指向传进来的对象，这是关键  
                      for(var i = start; i < end; i++){  
                           result.push(this[i]);  
                      }  
                      return result;  
                 }
```

#### 3) 转化
> - 利用slice方法 [].slice.call(a);
> - Array.from();
> - 手动转化
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                function transfer(obj) {
                    let arr = [];
                    let l = obj.length;
                    while(l > 0) arr[--l] = obj[l];
                    return arr;
                }
```
                    
### 2.4 数组乱序
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                shuffle = function(arr) {
                    let temp = 0;
                    let l = arr.length;
                    let r = 0;
                    for (let i = 0; i<l; i++) {
                        r = Math.floor(Math.random() * (i + 1));
                        temp = arr[r];
                        arr[r] = arr[i];
                        arr[i] = temp;
                    }
                }
                arr = [1,2,3,4,5,6];

                shuffle(arr);
                //[1, 4, 3, 5, 2, 6]
```

                        
### 2.8 ajax封装
        
        
#### 1) 功能
> - 
> - 

### 2.9 String.format
        
        
#### 1) 功能
> - 是一个函数挂载到String的原型上
> - 相当于字符串模板
> - 参数是模板的数据
> - 分别用两个正则表达式切割关键词和非关键词，然后在进行拼接
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                String.prototype.iFormat = function(data) {
                    let keyArray = this.match(/(?<=\$\{)\S+?(?=\})/g);
                    let strArray = this.split(/\$\{\S+?\}/g);
                    return strArray.map((item, index) => data[keyArray[index]] ? item + data[keyArray[index]] : item).join('');
                }

                let str = "${a}ads${a}sad${b}as${c}zx${c}";
                str.iFormat({a: ' I ', b: ' love ', c: ' you '}); //" I ads I sad love as you zx you "
```

#### 2) 一个更加简介的办法：利用replace()
> - 第二个参数可以是函数，将每匹配到的一组分组就执行一次
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                String.prototype.iFormat = function(transfer)   {
                    return this.replace(/\$\{.+?\}/g, function(group){
                        return transfer[group.replace(/(^\$\{)|(\}$)/g, '')];
                    })
                }

                let str = "${a}ads${a}sad${b}as${c}zx${c}";
                str.iFormat({a: ' I ', b: ' love ', c: ' you '});
                // " I ads I sad love as you zx you "
```

### 2.10 String.thousandSplit
           
#### 1) 功能
> - 西方的数字从右往左每三位加一个分隔符
#### 2) 实现
> - 需要零宽正向预言
> - $表示从右往左
> - ，不能放在第一位
> - 需要全局判断，因为不止匹配一个
```js
            /**
             * 
             * @authors ${冰红茶} (${hblvsjtu@163.com})
             * @date    2019-08-01
             * @version $Id$
             */

            String.prototype.thousandSplit = function(tag) {
                return this.replace(/(?<=\B)(?=(\d{3})+$)/g, tag);
            }

            '234123456'.thousandSplit(',');
            // "234,123,456"
            '1234123456'.thousandSplit('$');
            // "1$234$123$456"
```

        
------      
        
## 三、原理实现篇
### 3.1 call/apply/bind

        
#### 1) call
> - 返回一个立即执行的函数
> - 该函数的作用域被绑定为第一个形参
> - 其他的形参作为原函数的参数
> - 模拟的方法被绑定在函数的原型上，方便调用
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                function myCall(fn, context = window, ...ret) {
                    const symbol = Symbol();
                    context[symbol] = fn;
                    const result = context[symbol](...ret);
                    delete context[symbol];
                    return result;
                }

```

#### 2) apply
> - 根据call把参数改成数组输入的形式
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                Function.prototype.myApply = function(content) {
                    content.func = this; //转移this
                    return content.func(...arguments[1]);
                }

                let a = function(num1, num2) {
                    this.num = this.num ? this.num + num1 : num2;
                    console.log(this.num);
                }

                let b = {num: 1};

                a.myApply(b, [2, 3]);

                // 3
```

#### 3) bind
> - 返回一个函数
> - 函数的作用域为bind的第一个参数
> - 如果bind的参数不足够原函数消化，剩余的参数可以在返回的函数中输入
> - 作为原型挂靠在Function上
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                Function.prototype.myBind = function() {
                    let self = this;
                    let arr1 = Array.from(arguments);
                    return function() {
                        let arr2 = arr1.concat(Array.from(arguments));
                        return self.call(...arr2);
                    }
                }

                let a = function(num1, num2) {
                    this.num = this.num ? this.num + num1 + num2 : num2;
                    console.log(this.num);
                }

                let b = {num: 1};

                let c = a.myBind(b, 2);

                c(3);

                //6
                c(3);
                11
                c(3);
                16
```

### 3.2 Deferred和Promise

        
#### 1) promise/A规范
> - 一个Promise对象有三种状态：未完成pendding，已完成Fulfilled和已拒绝Rejected
> - pendding可以转化成Fulfilled或者Rejected，但Fulfilled和Rejected不能相互转化
> - 转化的过程是不可逆的
> - 使用then方法可以返回promise进行链式调用
> - then方法的onFulfilled,onRejected 方法都是可选参数，且不是function，都被忽略
#### 2) Deferred/promise
> - 这两个是合在一起的，这里的promise非ES6里面的Promise对象，注意这里的p是小写
> - Deferred更像是一个触发器
> - promise的then方法用来传递handlerQueue序列，handlerQueue是由每个then方法里面resolve和reject组成的handler集合
> - Deferred的resolve和reject遍历handlerQueue序列里面的handler，如果返回的结果是一个promise，就的Deferred的promise更新为返回的结果，如果不是的话就将结果作为下次resolve的实参。注意的是每遍历一个元素都需要把handlerQueue去掉相应的handler
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                let promise = function() {
                    this.handlerQueue = [];
                }

                promise.prototype.then = function(resolve, reject) {
                    let handler = {};
                    if(resolve && typeof resolve === 'function') 
                        handler.resolve = resolve;
                    if(reject && typeof reject === 'function') 
                        handler.reject = reject;
                    this.handlerQueue.push(handler);
                    return this;
                }

                let Deferred = function() {
                    this.state = 'pending';
                    if(!this.promise) {
                        this.promise = new promise();
                    }
                }

                Deferred.prototype.resolve = function(data) {
                    this.state = 'resolve';
                    let handlerQueue = this.promise.handlerQueue;
                    let res;
                    let handler;
                    while(handler = handlerQueue.shift()) {
                        if (handler && handler.resolve) {
                            res = handler.resolve(data);
                            if (res && res instanceof promise) {
                                res.handlerQueue = handlerQueue;
                                let p = new promise();
                                p.handlerQueue = handlerQueue;
                                this.promise = p;
                            }
                            else if(res) {
                                data = res;
                            }
                        }
                    }
                }

                Deferred.prototype.reject = function(data) {
                    this.state = 'reject';
                    let handlerQueue = this.promise.handlerQueue;
                    let res;
                    let handler;
                    while(handler = handlerQueue.shift()) {
                        if (handler && handler.reject) {
                            res = handler.reject(data);
                            if (res && res instanceof promise) {
                                res.handlerQueue = handlerQueue;
                                this.promise = res;
                                return; // 这里还是有问题，如果返回的是一个promise会直接中断运行
                            }
                            else if(res) {
                                data = res;
                            }
                        }
                    }
                }

                //------ test-------//
                function asyncDosomeing(flag, name) {
                    const deferred = new Deferred()
                    setTimeout(function () {
                        if (flag) {
                            deferred.resolve({code: 200, message: '成功', name: name})
                        } else {
                            deferred.reject({code: 400, message: '失败', name: name})
                        }
                    }, 2000)
                    return deferred.promise
                }
                asyncDosomeing(true, 'asyncDosomeing1').then(result => {
                    console.info(result)
                    return asyncDosomeing(false, 'asyncDosomeing2')
                }).then(result => {
                    console.info(result)
                    return 'dadds'
                }).then(result => {
                    console.info(result)
                })
```

#### 2) Promise(第一次自己写的)
> - Promise是Deferred/promise的混合版
> - Promise既作触发器又做储存器
> - 需要在resolve和reject上包装，已达到窃听的效果
> - 实现resolve和reject原型方法
> - 如果返回值是空类型，则正常返回this作链式调用，如果返回值非空也非Promise类型，则作为参数传到下一个then，可惜这个我实现不了
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */
                let MyPromise = function(fn) {
                    this.status = 'unfulfilled';
                    this.fn = typeof fn === 'function' ? fn : function() {};
                    this.resolve = function(func) {
                            let newPromise = new Promise(func);
                            newPromise.status = 'fulfilled';
                            return newPromise;
                    }

                    this.reject = function(func) {
                            let newPromise = new Promise(func);
                            newPromise.status = 'failed';
                            return newPromise;
                    }
                }
                MyPromise.prototype.then = function(resolve, reject) {
                    let self = this;
                    this.resolve = resolve;
                    this.reject = reject;
                    let _resolve = function(a) {
                        self.status = 'fulfilled';
                        resolve(a);
                    }
                    let _reject = function(a) {
                        self.status = 'failed';
                        reject(a);
                    }
                    if (this.status === 'unfulfilled') 
                            this.fn(_resolve, _reject);
                    if (this.status === 'fulfilled') 
                            this.fn(resolve);
                    if (this.status === 'failed') 
                            this.fn(reject);
                    return this;
                }

                p = function(value) {
                    return new MyPromise((resolve, reject) => {
                        setTimeout(function() {
                            if (value < 10) {
                                resolve(value);
                            }
                            else {
                                reject(value);
                            }
                        }, 1000)
                    })
                }
                p(9)
                .then(data => {
                        console.log('fulfilled = ', data);
                    }, data => {
                        console.log('unfulfilled = ', data);
                    })
                .then(data => {
                        console.log('transfer..');
                        return data + 10;
                    })
                .then(data => {
                        console.log('fulfilled = ', data);
                    }, data => {
                        console.log('unfulfilled = ', data);
                    })
                MyPromise.resolve((resolve) => {
                    setTimeout(function() {
                            resolve('i love you');
                    }, 1000)
                }).then(data => {
                        console.log('fulfilled = ', data);
                    })
```

#### 3) Promise(看了别人代码后自己写的)
> - 为了支持同步的Promise，采用异步调用_resolve和_reject
> - then方法比较复杂，首先返回的是一个promise，然后根据不同的返回值类型进行进一步处理
> - function(cal) {try {resolve(val) or reject(val)} catch(e) {reject(e)}}
> - catch是唯一没有可能返回promise的函数
> - resolve和reject方法就是返回一个仅有resolve或者reject方法的promise，同时resolve方法将判断参数的类型，如果参数是非promise类型，将会把它包装成promise类型
> - all方法是返回一个promise，循环得到结果放到一个数组中，由于每个子项执行的时间不一致，只能新建计数器来统计then执行的次数，当计数器等于all的数组参数个数的时候才进行resolve的统一处理结果数组
> - race方法是返回一个promise，遍历所有的promise数组，不需要搜集结果
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                // 定义状态常量
                const PENDDING = 'pendding';
                const FULFILLED = 'fulfilled';
                const UNFULFILLED = 'unfulfilled';

                // 判断是否是函数类型
                let isFunction = function (func) {
                    return typeof func === 'function'
                };

                class MyPromise {

                    constructor(handle) {

                        // 判断handle是否是函数
                        if (!isFunction(handle)) {
                            throw new Error('Your handle is not function!')
                        }

                        // 定义初始状态
                        this._status = PENDDING;

                        // 定义每次执行函数的参数
                        this._value = undefined;

                        // 定义resolve队列和reject，用于链式调用
                        this._resolveQueue = [];
                        this._rejectQueue = [];

                        // 执行handle;
                        try {
                            handle(this._resolve.bind(this), this._reject.bind(this));
                        }
                        catch(err) {
                            this._reject(err);
                        }
                    }

                    // 添加resolve时执行的函数
                    _resolve(val) {

                        // 判断此时的状态，如果是非PENDDING状态就直接结束
                        if (this._status !== PENDDING) return;

                        let run = function() {
                            // 执行队列
                            let execQueue = function(queue, argu) {
                                let exec;
                                while(exec = queue.shift()) {
                                    exec(argu);
                                }
                            }

                            // 判断val是否是MyPromise类型
                            // 如果val是MyPromise类型则执行它
                            // 如果val不是MyPromise类型则
                            if (val instanceof MyPromise) {
                                val.then(value => {
                                    this._value = value;
                                    this._status = FULFILLED;
                                    execQueue(this._resolveQueue, this._value);
                                }, error => {
                                    this._value = error;
                                    this._status = UNFULFILLED;
                                    execQueue(this._rejectQueue, this._value);
                                })
                            }
                            else {
                                this._value = val;
                                this._status = FULFILLED;
                                execQueue(this._resolveQueue, this._value);
                            }
                        }

                        // 为了支持同步的Promise，这里采用异步调用
                        setTimeout(run.bind(this), 0);
                    }  

                    // 添加reject时执行的函数
                    // 此时不需要判断参数类型是否是MyPromise类型
                    _reject(error) {

                        // 判断此时的状态，如果是非PENDDING状态就直接结束
                        if (this._status !== PENDDING) return;

                        let run = function() {
                            // 执行队列
                            let execQueue = function(queue, argu) {
                                let exec;
                                while(exec = queue.shift()) {
                                    exec(argu);
                                }
                            }

                            this._value = error;
                            this._status = UNFULFILLED;
                            execQueue(this._rejectQueue, this._value);
                        }

                        // 异步执行
                        setTimeout(run.bind(this), 0);
                    }

                    // 添加then方法 用于承上启下
                    // 当状态是PENDDING时保存每个状态的方法到相应队列
                    // 返回的是一个MyPromise
                    then(onFulfilled, onRejected) {
                        // 初始化变量
                        const _value = this._value;
                        const _status = this._status;

                        // onFulfilledNext, onRejectedNext为下一个then中的回调函数
                        return new MyPromise((onFulfilledNext, onRejectedNext) => {

                            // 封装一个可以执行一系列判断的onFulfilled
                            let fulfilled = function(_value) {
                                try {
                                    if(isFunction(onFulfilled)) {  //判断onFulfilled是否是函数
                                        let res = onFulfilled(_value);
                                        if(res instanceof MyPromise) { // 假如res是一个MyPromise类型，则需要等res执行完毕才能跳到下一个状态
                                            res.then(onFulfilledNext, onRejectedNext);
                                        }
                                        else { // 假如res不是一个MyPromise类型，则作为下一个then中回调函数中的参数
                                            onFulfilledNext(res);
                                        }
                                    }
                                    else { // 如果onFulfilled不是函数
                                        onRejectedNext(_value);
                                    }
                                }
                                catch (err) {
                                    onRejectedNext(err);
                                }
                            }

                            // 封装一个可以执行一系列判断的onRejected
                            let rejected = function(_value) {
                                try {
                                    if(isFunction(onRejected)) { // 如果onRejected是函数
                                        let res = onRejected(_value); 
                                        if(res instanceof MyPromise) { // 假如res是一个MyPromise类型，则需要等res执行完毕才能跳到下一个状态
                                            res.then(onFulfilledNext, onRejectedNext);
                                        }
                                        else {  // 假如res不是一个MyPromise类型，则作为下一个then中回调函数中的参数
                                            onFulfilledNext(res);
                                        }
                                    }
                                    else { // 如果onRejected不是函数
                                        onRejectedNext(_value);
                                    }
                                }
                                catch (err) {
                                    onRejectedNext(err);
                                }
                            }

                            // 判断_status的状态才决定执行怎样的处理函数
                            switch (_status) {
                                case PENDDING: // 如果是PENNDING的话把onFulfilled和onRejected保存到队列中
                                    this._resolveQueue.push(fulfilled);
                                    this._rejectQueue.push(rejected);
                                    break
                                case FULFILL: // 如果是FULFILL状态，则马上执行onFulfilled
                                    fulfilled(_value);
                                    break   
                                case UNFULFILL:  // 如果是UNFULFILL状态，则马上执行onRejected
                                    rejected(_value);
                                    break
                            }
                        })
                    }
                    static resolve(val) {
                        return val instanceof MyPromise ? val : new MyPromise((resolve, reject) => {
                            resolve(val);
                            })
                    }
                    static reject(err) {
                        return new MyPromise((resolve, reject) => {
                            reject(err);
                        })
                    }

                    static catch(rejected) {
                        return this.then(undefined, rejected);
                    }

                    static all(promiseArr) {
                        let res = [];
                        let num = 0;
                        return new MyPromise((resolve, reject) => {
                            promiseArr.forEach(item => {
                                this.resolve(item).then(argu => {
                                    res.push(argu);
                                    num++;
                                    if (num === promiseArr.length)
                                        resolve(res)
                                }, error => reject(error))
                            })
                        });
                    }

                    static race(promiseArr) {
                        return new MyPromise((resolve, reject) => {
                            promiseArr.forEach(item => {
                                this.resolve(item).then(res => resolve(res), err => reject(err));
                            })
                        })
                    }
                }

                p = function(value) {
                    return new MyPromise((resolve, reject) => {
                        setTimeout(function() {
                            if (value < 10) {
                                resolve(value);
                            }
                            else {
                                reject(value);
                            }
                        }, 1000)
                    })
                }

                p(9)
                .then(data => {
                        console.log('fulfilled = ', data);
                        return data;
                    }, data => {
                        console.log('unfulfilled = ', data);
                    })
                .then(data => {
                        console.log('transfer..');
                        return p(data + 10);
                    })
                .then(data => {
                        console.log('fulfilled = ', data);
                    }, data => {
                        console.log('unfulfilled = ', data);
                    })

                // 结果
                fulfilled =  9
                VM17445:9 transfer..
                VM17445:15 unfulfilled =  19

                let pTime = function(value, delay) {
                    return new MyPromise((resolve, reject) => {
                        setTimeout(function() {
                            if (value < 10) {
                                resolve(value);
                            }
                            else {
                                reject(value);
                            }
                        }, delay)
                    })
                }

                MyPromise.race([pTime(9, 5000), pTime(8, 3000), pTime(7, 1000)]).then(data => {
                    console.log('fulfilled = ', data);
                }, data => {
                    console.log('unfulfilled = ', data);
                }) 

                //fulfilled =  7

                MyPromise.race([pTime(18, 5000), pTime(19, 3000), pTime(20, 1000)]).then(data => {
                    console.log('fulfilled = ', data);
                }, data => {
                    console.log('unfulfilled = ', data);
                })

                // unfulfilled =  20

                MyPromise.all([pTime(7, 5000), pTime(8, 3000), pTime(9, 1000)]).then(data => {
                    console.log('fulfilled = ', data);
                }, data => {
                    console.log('unfulfilled = ', data);
                })

                // fulfilled =  (3) [9, 8, 7]
```
                
                        
### 3.4 观察者模式
                
#### 1) 要点
> - 监听器listener：其实是一系列的函数
> - 监听器类型: type
> - 监听器注册表：
```js
                let _registers = [
                                    {
                                        type: '',
                                        listener: ''
                                    },
                                    ...
                                ]
```

> - 监听器列表：
```js
                
                let _listeners = {
                    type1: [
                            listener1,
                            listener2,
                            ...
                    ],
                    type2: [
                            listener1,
                            listener2,
                            ...
                    ],
                    ...
                }
```

> - 建立一个类
>> - 原型变量:注册表和监听器列表
>> - 原型方法：添加/删除 某类型的监听器
                
                
#### 2) 代码
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                let Listen = function() {

                }
                Listen.prototype = {
                    _listeners: {},
                    _registers: [],
                    addListener: function(type, listener) {
                        this._listeners[type] = this._listeners[type] ? this._listeners[type] : [];
                        this._listeners[type].push(listener);
                    },
                    removeListener: function(type, listener) {
                        let index = this._listeners[type].indexOf(listener);
                        if (index >= 0) {
                            this._listeners[type].splice(index,index+1);
                        }
                    },
                    register: function(type, listener) {
                        this._registers.push(
                            {
                                type: type,
                                listener: listener
                            }
                        )
                    },
                    trigger: function(type, var_args) {
                        let funcs = this._listeners[type];
                        let args = [].slice.call(arguments, 1);
                        return funcs.map(func => func.apply(this, args));
                    }
                }
                Listen.prototype.contructor = Listen;
```
                        
### 3.5 防抖动和截流
                
#### 1) 相同点
> - 防止用户频繁的操作造成阻塞或者屏幕抖动，提升用户体验
> - 提升性能
#### 2) 不同点
> - 防抖动是发生在操作与操作之间的时间空隙，拉长操作之间的延迟时间
> - 截流是指在连续重复的操作中，保证每次的操作时间周期，一般比操作实际运行的时间要长
#### 3) 防抖动
> - 最多存活一个，可能是第一个也有可能是最后一个
> - 需要用到setTimeout
> - 用bounce对回调函数进行包装
> - 注意setTimeout和的作用域：内部延迟执行的代码中的this永远指向window，但是回调函数本身的this可以指向其他，所以setTimeout需要先在全局进行定义。
```js
        /**
         * 
         * @authors ${冰红茶} (${hblvsjtu@163.com})
         * @date    2019-08-01
         * @version $Id$
         */
        function debounce(cb, delay, isImmediate) {
            let timer; //   利用闭包设置定时器，同时肩负是否立即执行的状态
            return function(...ret) { // 返回函数
                if (isImmediate) {
                    if (timer) clearTimeout(timer);
                    else cb(...ret);
                    timer = setTimeout(function() {
                        timer = null;
                    }, delay)
                }
                else {
                    if (timer) clearTimeout(timer);
                    timer = setTimeout(function() {cb(...ret);}, delay)
                }
            }
        }

        a = debounce(function() {console.log(123)}, 2000, true);
        document.addEventListener('click', a);
```

#### 4) 截流/频率控制
> - 需要比较实际运行时间长度和设定的周期时间
> - 立即执行，无需使用setTimeout
> - 如果实际运行时间长度 > 设定的周期时间, 则运行回调，并且把当前时间戳设为旧时间戳；
```js
        /**
         * 
         * @authors ${冰红茶} (${hblvsjtu@163.com})
         * @date    2019-08-01
         * @version $Id$
         */
        function throttle(cb, delay, isImmediate) {
            let timer; //   利用闭包设置定时器，同时肩负是否立即执行的状态
            return function(...ret) { // 返回函数
                if (isImmediate) {
                    if (!timer) {
                        cb(...ret);
                        timer = setTimeout(function() {
                            timer = null;
                        }, delay);
                    }
                }
                else {
                    if (!timer) {
                        timer = setTimeout(function() {
                            cb(...ret);
                            timer = null;
                        }, delay);
                    }
                }
            }
        }

        a = throttle(function() {console.log(123)}, 2000, true);
        document.addEventListener('click', a);
```

#### 5) 防抖动和截流合并
> - 在截流里面把防抖动的函数写进去
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                let old = new Date();
                let myTimer;
                let bounceAndThrottle = function(cycleTime, delayTime, callback) {
                    let now = new Date();
                    if (now - old > cycleTime) {
                        console.log('Flow。。。');
                        clearTimeout(myTimer);
                        myTimer = setTimeout(function() {
                                if(callback) callback()
                            }, delayTime);
                        old = now;
                    }
                }

                document.addEventListener('click', function() {
                    debounceAndThrottle(3000, 5000, function() {
                            console.log('i am working');
                        });
                });
```
                        
### 3.6 类的继承
                
#### 1) 属性拷贝
> - 这是最简单的，把父类的属性全都拷贝一份
#### 2) 原型式继承
> - 只能继承父构造函数的原型对象上的成员, 不能继承父构造函数的实例对象的成员
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                // 父类
                function Parent(age) {
                    this.age = age;
                    this.friends = ['a', 'b'];
                }
                Parent.prototype.name = ['lvweiyaun'];
                Parent.prototype.tellName = function() {
                    console.log(this.name);
                }

                // 子类
                function Child(sex) {
                    this.sex = sex;
                }
                Child.prototype = Parent.prototype;
                Child.prototype.constructor = Child;
                let child1 = new Child('male');
                console.log('child1.name = ', child1.name);
                console.log('child1.friends = ', child1.friends);

                // child1.name =  ["lvweiyaun"]
                // undefined
```

#### 3) 原型链继承
> - 将父类的公有和私有属性和公有方法都继承过来的
> - 优点：直接把父类的原型（浅）拷贝过来，简单易用
> - 缺点
>> - 新实例无法向父类构造函数传参
>> - 存在父类私有引用类型属性共享的问题
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                // 父类
                function Parent(age) {
                    this.age = age;
                    this.friends = ['a', 'b'];
                }
                Parent.prototype.name = ['lvweiyaun'];
                Parent.prototype.tellName = function() {
                    console.log(this.name);
                }

                // 子类
                function Child(sex) {
                    this.sex = sex;
                }
                Child.prototype = new Parent(50);
                Child.prototype.constructor = Child;
                let child1 = new Child('male');
                console.log('child1.friends = ', child1.friends);
                let child2 = new Child('female');
                console.log('child2.friends = ', child2.friends);
                child2.friends.push('lvhongbin');
                console.log('child2.friends = ', child2.friends);
                console.log('child1.friends = ', child1.friends);

                // child1.friends =  ["a", "b"]
                // child2.friends =  ["a", "b"]
                // child2.friends =  ["a", "b", "lvhongbin"]
                // child1.friends =  ["a", "b", "lvhongbin"]
```

#### 4) 构造函数继承
> - 使用call继承父类的构造函数
> - 好处：可以得到父类的构造函数属性，向父类构造函数传参。
> - 坏处：无法得到父类的原型属性
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */
                // 父类
                function Parent(age) {
                    this.age = age;
                }
                Parent.prototype.name = ['lvweiyaun'];
                Parent.prototype.tellName = function() {
                    console.log(this.name);
                }

                // 子类
                function Child(sex, age) {
                    Parent.call(this, age);
                    this.sex = sex;
                }
                let child1 = new Child('male', 20);
                console.log('child1.name = ', child1.name);
                let child2 = new Child('female', 22);
                console.log('child2.name = ', child2.name);
                child2.name.push('lvhongbin');
                console.log('child2.name = ', child2.name);
                let p = new Parent(55);
                console.log('p.name = ', p.name);
                console.log('child1.name = ', child1.name);
                console.log('child1.age = ', child1.age);


                // child1.name =  undefined
                // child2.name =  undefined
                // error!
                p.name =  ["lvweiyaun"]
                // child1.name =  undefined
                child1.age =  20
```

#### 5) 组合继承
> - 原型链继承 + 构造函数继承
> - 解决了对象共享的问题，还能拿到父类的构造函数
> - 但是存在性能问题，因为父类有两次构造
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */
                // 父类
                function Parent(age) {
                    this.age = age;
                    this.friends = ['a', 'b'];
                }

                Parent.prototype.name = ['lvweiyaun'];
                Parent.prototype.tellName = function() {
                    console.log(this.name);
                }

                // 子类
                function Child(sex, age) {
                    Parent.call(this, age);
                    this.sex = sex;
                }
                Child.prototype = new Parent(50);
                Child.prototype.constructor = Child;
                let child1 = new Child('male', 20);
                console.log('child1.name = ', child1.name);
                console.log('child1.friends = ', child1.friends);
                let p = new Parent(55);
                console.log('p.name = ', p.name);
                console.log('child1.name = ', child1.name);
                console.log('child1.age = ', child1.age);


                // child1.name =  ["lvweiyaun"]
                // child1.friends =  ["a", "b"]
                // p.name =  ["lvweiyaun"]
                // child1.name =  ["lvweiyaun"]
                // child1.age =  20
```

#### 6) 组合继承优化1
> - 原型式继承 + 构造函数继承
> - 解决了对象共享的问题，还能拿到父类的构造函数
> - 不存在性能问题
> - 但是子类无法修改原型的constructor属性，因为一旦修改就会同时修改父类的constructor属性，换句话说无法辨别子类的构造函数是谁
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */
                // 父类
                function Parent(age) {
                    this.age = age;
                    this.friends = ['a', 'b'];
                }
                Parent.prototype.name = ['lvweiyaun'];
                Parent.prototype.tellName = function() {
                    console.log(this.name);
                }

                // 子类
                function Child(sex, age) {
                    Parent.call(this, age);
                    this.sex = sex;
                }
                Child.prototype = Parent.prototype;
                Child.prototype.constructor = Child;
                
                let child1 = new Child('male', 20);
                console.log('child1.name = ', child1.name);
                console.log('child1.friends = ', child1.friends);
                let p = new Parent(55);
                console.log('p.name = ', p.name);
                console.log('child1.name = ', child1.name);
                console.log('child1.age = ', child1.age);
                p instanceof Child;


                // child1.name =  ["lvweiyaun"]
                // child1.friends =  ["a", "b"]
                // p.name =  ["lvweiyaun"]
                // child1.name =  ["lvweiyaun"]
                // child1.age =  20
                // true
```

#### 7) 组合继承优化2
> - 目前来讲比较完美的方法
> - 使用寄生式组合继承
```js
                // 父类
                function Parent(age) {
                    this.age = age;
                    this.friends = ['a', 'b'];
                }
                Parent.prototype.name = ['lvweiyaun'];
                Parent.prototype.tellName = function() {
                    console.log(this.name);
                }

                // 子类
                function Child(sex, age) {
                    Parent.call(this, age);
                    this.sex = sex;
                }
                Child.prototype = Object.create(Parent.prototype);
                Child.prototype.constructor = Child;

                let child1 = new Child('male', 20);
                console.log('child1.name = ', child1.name);
                console.log('child1.friends = ', child1.friends);
                let p = new Parent(55);
                console.log('p.name = ', p.name);
                console.log('child1.name = ', child1.name);
                console.log('child1.age = ', child1.age);
                p instanceof Child;

                // child1.name =  ["lvweiyaun"]
                // child1.friends =  ["a", "b"]
                // p.name =  ["lvweiyaun"]
                // child1.name =  ["lvweiyaun"]
                // child1.age =  20
                // false
```

### 3.7 new
                
#### 1) 要点
> - 创建一个空对象
> - 函数的作用域指向该对象
> - 对象获取函数的属性和方法
> - 返回新的对象(需要注意的是，假如函数返回的是一个对象，那么最终返回的不是之前创建的空对象，而是函数的返回值)
```js
                // 方法一
                function myNew(func, ...res) {
                    const obj = {};
                    obj.__proto__ = func.prototype;
                    const result = func.call(obj, ...res);
                    return typeof result === 'object' ? result : obj;
                }

                // 方法二
                function myNew(func, ...res) {
                    const obj = Object.create(func.prototype);
                    const result = func.call(obj, ...res);
                    return typeof result === 'object' ? result : obj;
                }

                // 方法三
                Function.prototype.myNew = function() {
                    let obj = {};
                    obj.__proto__ = this.prototype;
                    let argu = [].slice.call(arguments);
                    this.call(obj, ...argu);
                    return obj;
                }

                function a(num1, num2) {
                    this.num1 = num1;
                    this.num2 = num2;
                }
                a.prototype.tell = function() {
                    console.log(this.num1 + this.num2);
                }

                let b = a.myNew(1,2);
                b.tell(); // 3

                let c = new a(1,2);
```

>>>>>> ![图3-1 new原理](https://github.com/hblvsjtu/FET/blob/master/picture/%E5%9B%BE3-1%20new%E5%8E%9F%E7%90%86.png?raw=true)

### 3.8 Object.create()
                
#### 1) 参数
> - 第一个参数是原型对象
> - 第二个参数是属性特性：value, writable, enumberable, congigurable
```js
                Object.prototype.myCreate = function(proto, properties) {
                    let f = function() {};
                    f.prototype = proto;
                    let o = new f();
                    if (typeof properties === 'object') {
                        Object.defineProperties(o, properties);
                    }
                    return o;
                }
```

### 3.9 Object.keys/Object.values/Object.entries
                
#### 1) Object.keys
> - 返回对象的每个可枚举的自身属性键名组成的数组
```js
                Object.prototype.myKeys = function(o) {
                    let arr = []
                    for(let key in o) {
                        if(o.hasOwnProperty(key)) arr.push(key);
                    }
                    return arr;
                }
```

#### 2) Object.values
> - 返回对象的每个可枚举的自身属性键值组成的数组
```js
                Object.prototype.myValues = function(o) {
                    let arr = []
                    for(let key in o) {
                        if(o.hasOwnProperty(key)) arr.push(o[key]);
                    }
                    return arr;
                }
```

#### 2) Object.entrie
> - 返回对象的每个可枚举的自身属性键名和键值组成的数组
```js
                Object.prototype.myEntries = function(o) {
                    let arr = []
                    for(let key in o) {
                        if(o.hasOwnProperty(key)) arr.push([key, o[key]]);
                    }
                    return arr;
                }
```

### 3.10 setTimeout 与 setInterval
                
#### 1) 最短间隔时间
> - 如果回调时间大于间隔时间，浏览器才会执行，这也导致了真正的间隔时间比原来的大一点
> - 这个最短间隔时间该怎么测呢？可以利用在定时器内再嵌一个定时器
```js
                let timeList = [];
                let f = function(total, delay) {
                    let sum = 0;
                    let c = 0;
                    let id = setTimeout(function() {
                        c++;
                        timeList.push(new Date());
                        if(c > total) {
                            clearTimeout(id);
                            for(let i = 0; i < total - 1; i++) {
                                sum += timeList[i+1] - timeList[i];
                            }
                            console.log('the shortest delayTime is ', sum/(total - 1))
                        }
                        else setTimeout(arguments.callee, delay);
                    }, delay);
                }
                f(100, 1); // the shortest delayTime is 4.878787878787879 in chrome
                f(1000, 1); // the shortest delayTime is  83.83883883883884 in chrome
```

### 3.11 跨域
                
#### 1) 通过document.domain跨域
> - 在相同的域名下建立文件
#### 2) 通过location.hash跨域
> - 但是如果内嵌的页面不同源的话是无法拿到iframe的document的
```js
                let src = 'https://www.baidu.com';
                let msg = 'helloB'
                function createIframe(src) {    
                    let frag = document.createDocumentFragment();
                    let ifm = document.createElement('iframe');
                    ifm.src = src;
                    ifm.style.display = 'none';
                    frag.appendChild(ifm);
                    document.body.appendChild(frag);
                }

                function checkHash() {
                    return location.hash ? location.hash.slice(1) : '';
                }
                window.addEventListener("hashchange", function() {
                    console.log('hash has been changed, now hash is', checkHash());
                }, false);

                createIframe(src + '#' + msg);

                let i = document.getElementsByTagName('iframe')[ document.getElementsByTagName('iframe').length - 1];
                let ifmScript = document.createElement('script');
                ifmScript.innerHTML = ""
                    +  "let hash = location.hash ? location.hash.slice(1) : '';\n"
                    +  "let message = hash + 'helloA';\n"
                    +  "try {\n"
                    +  "  parent.location.hash = message;\n"
                    +  "  console.log('OK, i am done, message = ', message);\n"
                    +  "} catch (e) {\n"
                    +  "  // ie、chrome的安全机制无法修改parent.location.hash，\n"
                    +  "  // 所以要利用一个中间的cnblogs域下的代理iframe\n"
                    +  "  var ifrproxy = document.createElement('iframe');\n"
                    +  "  ifrproxy.style.display = 'none';\n"
                    +  "  ifrproxy.src = 'http://ecma.bdimg.com/adtest/limukai/demo/test/cscript/cs3.html#' + message;  \n"
                    +  "  // 注意该文件在a.com域下\n"
                    +  "  document.body.appendChild(ifrproxy);\n"
                    +  "  let i = document.getElementsByTagName('iframe')[ document.getElementsByTagName('iframe').length - 1];\n"
                    +  "  let ifmScript = document.createElement('script');\n"
                    +  "  ifmScript.innerHTML = 'parent.parent.location.hash = self.location.hash.substring(1);'\n"
                    +  "  ifrproxy.appendChild(ifmScript);\n"
                    + "}"
                i.contentWindow.document.body.appendChild(ifmScript);
```

#### 3) 通过postMessage
> - 好像也做不了
> - 需要判断源origin，否则容易收到XXR攻击
```js
                let msgHandler = function(event) {
                    console.log('event.data', event.data);
                }
                window.addEventListener('message', msgHandler, false);

                let src = 'https://www.baidu.com';
                let msg = 'helloB'
                function createIframe(src) {    
                    let frag = document.createDocumentFragment();
                    let ifm = document.createElement('iframe');
                    ifm.src = src;
                    ifm.style.display = 'none';
                    frag.appendChild(ifm);
                    document.body.appendChild(frag);
                }
                createIframe(src + '#' + msg);

                let i = document.getElementsByTagName('iframe')[ document.getElementsByTagName('iframe').length - 1];
                let iframe = i.contentWindow;
                iframe.postMessage('hello world', 'https://segmentfault.com/a/1190000012264815');
```

#### 4) Jsonp
> - 只支持GET，不支持POST请求
> - 它只支持跨域HTTP请求这种情况，不能解决不同域的两个页面之间如何进行JavaScript调用的问题。
> - 支持老版本的浏览器
```html
            // 自己的页面
            <script>
                function exec(data) {
                    console.log(data);
                }
            </script>
            <script src="http://www.baidu.com?callback=exec"></script>

            // 后端
                1，判断callback的名称；
                2，处理数据data
                3，返回js文件里面写着： exec(data);
```

#### 5) Access-Control-Allow-Origin
> - 存在兼容性的问题，不兼容老版本的浏览器
> - 服务器设置
```js   
                //指定允许其他域名访问
                'Access-Control-Allow-Origin:http://172.20.0.206'//一般用法（*，指定域，动态设置，但不允许携带认证头和cookies
                //是否允许后续请求携带认证信息（cookies）,该值只能是true,否则不返回
                'Access-Control-Allow-Credentials:true'
                //预检结果缓存时间
                'Access-Control-Max-Age: 1800'
                //允许的请求类型
                'Access-Control-Allow-Methods:GET,POST,PUT,POST'
                //允许的请求头字段
                'Access-Control-Allow-Headers:x-requested-with,content-type'
```

### 3.12 函数柯里化
                
#### 1) 定义
> - 一个函数接受一些参数后返回一个新的函数，这个新的函数继续接收剩余的参数
> - 比如：
```js     
                // 原函数
                function origin(a, b, c) {

                }

                // 柯里化
                function curry(a) {
                    return function(b, c) {

                    }
                }
```

#### 2) 两段不定参数版本
> - 
```js  
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */
                function curry() {
                    let args1 = [].slice.call(arguments);
                    return function() {
                        let args2 = [].slice.call(arguments);
                        argus = args1.concat(args2);
                        console.log(argus);
                    }
                }
                curry(1)(2); //[1, 2]
                curry(1,2)(2,3,4); //  [1, 2, 2, 3, 4]
```

#### 3) 不定段不定参数版本
> - 无限累加器
> - points
>> - 改写函数的toSting()和valueOf()方法
>> - 返回的函数作为参数收集器
>> - 真正做处理方法是toSting()和valueOf()方法
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */
                function curry() {

                    let args = [].slice.call(arguments);

                    let _curry = function() { 
                        let add = function() {
                            args.push(...arguments) // 为了搜集参数
                            return add;
                        }

                        add.toString = function() { // 输出结果
                            return args.reduce((total, item) => {
                                return total + item;
                            })
                        }
                        return add;
                    }

                    return _curry(...args);
                }
```
             
### 3.13 高阶函数
                
#### 1) 定义
> - 接受一个或多个函数作为输入
> - 输出一个函数
#### 2) 实现一个map函数
> - 挂靠在Array数组原型上
```js 
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */
                Array.prototype.myMap = function(func) {
                    let l = this.length;
                    let temp = [];
                    for(let i = 0; i < l; i++) {
                        temp[i] = func(this[i], i, this);
                    }
                    return temp;
                }
```

#### 3) 实现一个forEach函数
> - 挂靠在Array数组原型上
```js
        /**
         * 
         * @authors ${冰红茶} (${hblvsjtu@163.com})
         * @date    2019-08-01
         * @version $Id$
         */
        Array.prototype.myForEach = function(func) {
            let l = this.length;
            for(let i = 0; i < l; i++) {
                func(this[i], i, this);
            }
        }
```

#### 4) 实现一个reduce函数
> - 挂靠在Array数组原型上
```js
        /**
         * 
         * @authors ${冰红茶} (${hblvsjtu@163.com})
         * @date    2019-08-01
         * @version $Id$
         */
        Array.prototype.myReduce = function(func, init) {
            let result = init;
            for (var i = 0; i < this.length; i++) {
                result = func(result, this[i], i);
            }
            return result;
        }
```

#### 5) 实现一个filter函数
> - 挂靠在Array数组原型上               
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */
                Array.prototype.myFilter = function(func) {
                    let l = this.length;
                    let arr = [];
                    while(l--) if(func(this[l])) arr.unshift(this[l]);
                    return arr;
                }
```

             
### 3.14 迭代器
                
#### 1) 定义

```js
        function iterator() {
            let i = 0;
            let me = this;
            return {
                next() {
                    return {
                        value: me[i],
                        done: i++ >= me.length
                    }
                }
            }
        }
        a = {
            0: 0, 1: 1, 2: 2,
            length: 3,
            [Symbol.iterator]: iterator
        };

        for (i of a) {
            console.log(i);
        }
        // 0 1 2
```

            
### 3.15 instanceof
                
#### 1) 定义

```js
        // 递归版本
        function myInstanceof(left, right) {
            return !left
                ? false
                : left.__proto__ === right.prototype
                    ? true
                    : myInstanceof(left.__proto__, right);
        }

        // 循环版本
        function myInstanceof(left, right) {
            while(left && left.__proto__ !== right.prototype) {
                left = left.__proto__;
            }
            return !!left;
        }
```

------      
        
## 四、正则表达式
### 4.1 断言
            
#### 1) 定义
> - 断言前面或者后面有规定的字符串，但断言的字符串并不计入输出
#### 2) 类型
> - 向前断言 (?<=) (?<!)
> - 向后断言 (?=) (?!)
            
### 4.2 反向引用
            
#### 1) 定义
> - \数字 表示前面匹配到的第n个分组,改分组必须与前面的分组字面上一模一样
```js
                '168.132.132.132'.match(/(?:\d{1,3})(\.\d{1,3})\1{2}/);
                // ["168.132.132.132", ".132", index: 0, input: "168.132.132.132", groups: undefined]
```

#### 2) 要点
> - 非获取匹配分组 (?:)，用来忽视某个分组的
```js
                '168.131.31.1'.match(/(?:\d{1,3})(\d{1,3}\.)\1{2}/)
```
            
### 4.3 非贪婪
            
#### 1) 定义
> - 用在{1，2}，+,*等后面，匹配最小的那个数量
            
### 4.4 电话号码/身份证/网址/邮箱
            
#### 1) QQ号码
> - 对QQ号码进行校验要求5~11位,不能以0开头,只能是数字
```js
                /^[1-9]\d{4,10}$/.test('2606138901'); // true
                /^[1-9]\d{4,10}$/.test('0606138901'); // false
```

#### 2) 电话号码
> - 纯数字第一位必须是1开头第二位必须是3、4、5、7、8,第三位~第十一只要是数字即可
```js
                /^1[34578]\d{9}$/.test('18028543872'); // true
                /^1[34578]\d{9}$/.test('12028543872'); // false
```

#### 3) 身份证
> - 身份证号码为15位或者18位，15位时全为数字，18位前17位为数字，最后一位是校验位，可能为数字或者X或者x
```js
                /(^\d{15}$)|(^\d{17}[\dxX]$)/.test('440782199309241618'); // true
                /(^\d{15}$)|(^\d{17}[\dxX]$)/.test('44078219930924161X'); // true
                /(^\d{15}$)|(^\d{17}[\dxX]$)/.test('44078219930924161s'); // false
```

#### 3) 网址
> - DNS规定，域名中的标号都由英文字母和数字组成，每一个标号不超过63个字符，也不区分大小写字母。标号中除连字符（-）外不能使用其他的标点符号。级别最低的域名写在最左边，而级别最高的域名写在最右边。由多个标号组成的完整域名总共不超过255个字符。
```js
                /^[hH][tT]{2}[pP][sS]?:\/\/(www\.)?([\w\d-~]{1,63}\.)+([\w\d-~\/])+$/.test('https://www.baidu.com'); //true
```
#### 4) 邮箱
> - 
```js
                /^[a-zA-Z0-9]+@[a-zA-Z0-9]{1,5}\.[a-zA-Z0-9]{1,5}$/.test('supersteelsoul@163.com'); // true
```

        
------      
        
## 五、js和html效果篇
### 5.1 获取元素样式/位置/尺寸

        
#### 1) 样式
> - element.getAttribute()方法 只能获取内联样式的内容
```js
                var btn=element.getAttribute('style');
```

> - document.styleSheets 获取内嵌样式表或外联样式表，返回值是一个数组
```js           
                var styleSheetList = document.styleSheets;
                var styleSheet = styleSheetList[0];
                var cssRuleList = styleSheet.rules;
                var cssStyleRule = cssRuleList[0];
                var styleDecl = cssStyleRule.style;
                console.log(styleDecl.width);
```

> - class属性的操作
>> - className
>> - classList 兼容性问题。如果该类名不存在则会在元素中添加类名，并返回 true。 第二个是可选参数，是个布尔值用于设置元素是否强制添加或移除类，不管该类名是否存在.注意： Internet Explorer 或 Opera 12 及其更早版本不支持第二个参数。
```js
                //元素名.className 需要操作字符串,每个类中间用空格隔开
                var className = ele.className;
                className.replace('classNameA', '').replace(/\s+/g, ' ');
                className.concat(' classNameB').replace(/\s+/g, ' ');
                
                //classList属性(浏览器兼容问题)：获取多个类选择器叠加的用法
                //元素名.classList
                var classList = ele.classList;
                classList.add('className');
                classList.remove('className');
                classList.contains(class)
                classList.toggle(class, true|false) // 第一个参数为要在元素中移除的类名，并返回 false。
```

>> - 自定义类解决兼容性问题，可以兼容IE7
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */
                Object.prototype.myClassList = function() {
                    var self = this;
                    return {
                        list: self.className,
                        add: function(className) {
                            self.className = self.className.concat(' ' + className);
                        },
                        remove: function(className) {
                            self.className = self.className.replace(className, '');
                        },
                        contains: function(className) {
                            return self.className.split(/\s+/g).indexOf(className) > -1;
                        },
                        toggle: function(className) {
                            if(self.myClassList().contains(className)) {
                                self.myClassList().remove(className);
                            }
                            else {
                                self.myClassList().add(className);
                            }
                        }
                    }
                }

                //
                > div.listClass().list;
                < "s_tab"
                > div.listClass().add('asd');
                < undefined
                > div.listClass().list;
                < "s_tab asd"
                > div.listClass().remove('asd');
                < undefined
                > div.listClass().list;
                < "s_tab "
                > div.listClass().contains('asd');
                < false
                > div.listClass().contains('s_tab');
                < true
                > div.listClass().contains('s_ta');
                < false
                > div.listClass().toggle('s_ta');
                < undefined
                > div.listClass().contains('s_ta');
                < true
                > div.listClass().list;
                < "s_tab  s_ta" 
```

> - 获取实时计算的样式 getComputedStyle
>> - 只读的，不能写。
>> - 获取的是最终应用在元素上的所有CSS属性对象
>> - currentStyle不能读取伪类，但是getComputedStyle可以
>> - currentStyle是IE自娱自乐的玩意
>> - 在访问例如background-color类似格式的css属性时
```js
                window.getComputedStyle(ele,null).background-color //就不可以了，需要使用
                window.getComputedStyle(ele,null).backgroundColor //可以
                window.getComputedStyle(ele,null).getPropertyValue(“background-color”) // 可以
                
                var style = window.getComputedStyle("元素", "伪类");
                ele.currentStyle[attr]

                // 兼容性写法 如果遇到text的时候会报错，这里return null可以吃掉报错
                /**
                  * 
                  * @authors ${冰红茶} (${hblvsjtu@163.com})
                  * @date    2019-08-01
                  * @version $Id$
                  */

                Object.prototype.getMyStyle = function(attr, pseudoElt) {
                    let style = '';
                    try {
                        if(this.currentStyle) {
                            style = this.currentStyle[attr];
                        }
                        else {
                            style = window.getComputedStyle(this, pseudoElt)[attr];
                        }
                    }
                    catch (e) {
                        return null;
                    }
                    return style;
                }

                // ie7可能会返回auto值而不是实际的值
```

#### 2) 位置
> - 元素的位置
>> - ``getClientRects`` 返回一个数组，但是该数组只有一个元素，而且是一个对象元素，获取的是距离目标元素最近的父元素的距离
>> - ``offsetTop``,``offsetLeft``和``offsetParent``，而非视窗距离
>> - ``getBoundingClientRect``用于获取元素相对与浏览器视口的位置，它是一个对象
>> - 想要获取元素边内界边缘相对于文档顶部的距离，需要用到``getBoundingClientRect``或者递归``offsetTop``和``offsetLeft``
```js
        // getBoundingClientRect方法
        getBoundingClientRect: {
            top: '元素顶部相对于视口顶部的距离',
            bottom: '元素底部相对于视口顶部的距离',
            left: '元素左边相对于视口左边的距离',
            right: '元素右边相对于视口左边的距离',
            height: '元素高度',
            width: '元素宽度'
            x: 8,
            y: 8,
        }

        // 递归法
        function getDistance(node) {
            return node.parentNode ? getDistance(node.parentNode) + node.offsetTop : 0;
        }
```

>> - 兼容性写法 因为IE没有height和width
```js
                // 兼容写法
                 /**
                  * 
                  * @authors ${冰红茶} (${hblvsjtu@163.com})
                  * @date    2019-08-01
                  * @version $Id$
                  */

                  Object.prototype.getMyRect = function (isToHtml) {
                     var o = this.getBoundingClientRect();
                     var self = this;
                     var offset = function(ele) {
                        var parent = ele.offsetParent;
                        return {
                            top: isToHtml && parent.offsetParent? ele.offsetTop + offset(parent).top :  ele.offsetTop, 
                            left: isToHtml && parent.offsetParent ? ele.offsetLeft + offset(parent).left :  ele.offsetLeft
                        }
                     }
                     return {
                         viewTop: o.top, // 获取元素内边距边缘离视窗的距离
                         viewBottom: o.bottom, // 获取元素内边距边缘离视窗的距离
                         viewLeft: o.left, // 获取元素内边距边缘离视窗的距离
                         viewRight: o.right, // 获取元素内边距边缘离视窗的距离
                         height: o.height || o.bottom - o.top, // 获取元素上下内边缘高度，不包括边距
                         width: o.width || o.right - o.left, // 获取元素上下内边缘宽度，不包括边距
                            offsetTop: offset(self).top, //获取元素内边缘距离定位父元素的距离
                            offsetLeft: offset(self).left //获取元素内边缘距离定位父元素的距离
                     }
                 }
```

>> - 一个例子
```js
                // main.html
                <div class="contain">
                    <div class="camera">
                        <div class="cube"></div>
                    </div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */

                .contain {
                    position: relative;
                    top: 100px;
                    left: 100px;
                    height: 500px;
                    width: 500px;
                    overflow: scroll;
                    background: yellow;
                }

                 .camera {
                    position: absolute;
                    top: 400px;
                    left: 400px;
                    width: 200px;
                    height: 200px;
                    background: red;
                 }
                 .camera .cube {
                    width: 100px;
                    height: 100px;
                    margin: 50px;
                    background: green;
                 }

                 let contain = document.getElementsByClassName('contain')[0];
                 let camera = document.getElementsByClassName('camera')[0];
                 let cube = document.getElementsByClassName('cube')[0];
                 let camera = document.getElementsByClassName('camera')[0];
```

>>>>>> ![图5-1 元素位置a](https://github.com/hblvsjtu/FET/blob/master/picture/%E5%9B%BE5-1%20%E5%85%83%E7%B4%A0%E4%BD%8D%E7%BD%AEa.png?raw=true)
>>>>>> ![图5-1 元素位置b](https://github.com/hblvsjtu/FET/blob/master/picture/%E5%9B%BE5-1%20%E5%85%83%E7%B4%A0%E4%BD%8D%E7%BD%AEb.png?raw=true)
>>>>>> ![图5-1 元素位置c](https://github.com/hblvsjtu/FET/blob/master/picture/%E5%9B%BE5-1%20%E5%85%83%E7%B4%A0%E4%BD%8D%E7%BD%AEc.png?raw=true)
>>>>>> ![图5-1 元素位置d](https://github.com/hblvsjtu/FET/blob/master/picture/%E5%9B%BE5-1%20%E5%85%83%E7%B4%A0%E4%BD%8D%E7%BD%AEd.png?raw=true)
            
> - 滚动条滚动的距离
>> - 所有主流浏览器都支持 pageXOffset 和 pageYOffset 属性。注意： IE 8 及 更早 IE版本不支持该属性,但可以使用"document.body.scrollLeft" 和 "document.body.scrollTop" 属性 。
>> - chrome可以使用document.documentElement.scrollLeft和document.documentElement.scrollTop,或者window.pageXoffset与window.pageYoffset。
>> - 不管怎样，document.documentElement.scrollTop和document.body.scrollTop只有一个有效，另外一个为0，我们可以利用这一个特点写兼容性
>> - chrome里面的document.body.scrollHeight和document.body.scrollWidth偏小，而document.documentElement.scrollHeight和document.documentElement.scrollWidth正常，且IE也能用，所以就使用document.documentElement.scrollHeight和document.documentElement.scrollWidth吧
> - 视窗高度和宽度
>> - 视窗高度window.innerHeight
>> - 视窗宽度window.innerWidth
> - 元素内边距边缘距离文档顶部的距离
>> - offsetTop 和 offsetLeft 都是相对于其内边距边界的。
>> - HTMLElement.offsetParent 是一个只读属性，返回一个指向最近的定位父元素。如果没有定位的元素，则指向最近的 table 元素或根元素（标准模式下为 html；quirks 模式下为 body）。当元素的 style.display 设置为 "none" 时，offsetParent 返回 null。
```js
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */
                // 兼容性写法
                window.getWindowSize = function (doc) {
                    let myDocument = doc || document;
                    return {
                        scrollTop: myDocument.documentElement.scrollTop || myDocument.body.scrollTop,
                        scrollLeft: myDocument.documentElement.scrollLeft || myDocument.body.scrollLeft,
                        wholeHeight: myDocument.documentElement.scrollHeight,
                        wholeWidth: myDocument.documentElement.scrollWidth,
                        innerHeight: window.innerHeight,
                        innerWidth: window.innerWidth,
                        outerHeight: window.outerHeight,
                        outerWidth: window.outerWidth
                    }
                }
```

### 5.2 拖拽

        
#### 1) 行内元素
> - 
### 5.3 图片懒加载

        
#### 1) 行内元素
> - 
### 5.4 轮播

        
#### 1) 行内元素
> - 
### 5.5 滑动

        
#### 1) 行内元素
> - 
### 5.6 级联

        
#### 1) 行内元素
> - 
### 5.7 图片剪裁

        
#### 1) 行内元素
> - 
### 5.8 图片压缩

        
#### 1) 行内元素
> - 
### 5.9 Tab

        
#### 1) 行内元素
> - 

        
------      
        
## 六、CSS效果篇
### 6.1 水平居中

        
#### 1) 行内元素
> - 父元素上text-align: center;
```html
                // main.html
                <div class="contain">
                    <span class="centerText">我是居中的行内元素</span>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    text-align: center;
                    background: #000;
                }

                 .centerText {
                    background: #fff;
                }
```

#### 2) 块级元素
> - 定宽居中
>> - 自身元素上margin: auto; 一定要写width;
```html
                // main.html
                <div class="contain">
                    <div class="centerBlock">我是居中的块级元素</div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    background: #000;
                }

                .centerBlock {
                    width: 100px;
                    margin: auto;
                    background: #fff;
                } 
```

> - inline-block不定宽居中
>> - 把块状元素的显示值设置为inline-block
>> - 然后使用行内元素的text-align: center;
```html
                // main.html
                <div class="contain">
                    <div class="centerBlock">我是居中的块级元素</div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    text-align: center;
                    background: #000;
                }

                .centerBlock {
                    display: inline-block;
                    background: #fff;
                }
```

> - 绝对定位不定宽居中
>> - 注意IE8及以下不支持transform，其他的也需要加后缀
```html
                // main.html
                <div class="contain">
                    <div class="centerBlock">我是居中的块级元素</div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    position: relative;
                    background: #000;
                }

                .centerBlock {
                    display: inline-block;
                    position: absolute;
                    left: 50%;
                    transform: translateX(-50%);
                    background: #fff;
                }
```

> - table-cell不定宽居中
>> - 注意table-cell的特性有点像inline-block，需要设置width，而且不接受百分比，只接受数值，table-cell
>> - IE6 IE7无效
```html
                // main.html
                <div class="contain">
                    <div class="centerBlock">我是居中的块级元素</div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    display: table-cell;
                    width: 400px;
                    text-align: center;
                    background: #000;
                }

                .centerBlock {
                    display: inline-block;
                    background: #fff;
                } 
```


### 6.2 垂直居中

        
#### 1) 行内元素
> - 父元素需要设置行高
> - 自身元素上设置vertical-align
```html
                // main.html
                <div class="contain">
                    <span class="centerText">我是居中的行内元素</span>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    line-height: 400px;
                    vertical-align: middle;
                    background: #000;
                }

                 .centerText {
                    background: #fff;
                }
```

#### 2) 块级元素
> - line-height不定高居中
>> - 父元素需要设置行高，高度将被行高顶起，相当于设了高度
>> - 子元素设置vertical-align: middle，这是因为子元素被设为inline-block后，其基线将于内部文字的中线重合
>> - 由于父元素的行高等于自身高度，而子元素的基线在内部文字的中线上，所以就变成竖直居中了
>> - 会存在幽灵空白节点的问题，详细看[6.5 消除幽灵空格](#6.5)
```html
                // main.html
                <div class="contain">
                    <div class="centerBlock">我是居中的块级元素</div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    line-height: 100px;
                    background: #000;
                }

                .centerBlock {
                    display: inline-block;
                    line-height: 1;
                    vertical-align: middle; 
                    background: #fff;
                }
```

> - 绝对定位不定高居中
>> - 注意IE8及以下不支持transform，其他的也需要加后缀
>> - 父元素需要设置高度
```html
                // main.html
                <div class="contain">
                    <div class="centerBlock">我是居中的块级元素</div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    position: relative;
                    height: 100px;
                    background: #000;
                }

                .centerBlock {
                    display: inline-block;
                    position: absolute;
                    top: 50%;
                    transform: translateY(-50%);
                    background: #fff;
                }
```

> - table-cell不定高居中
>> - 注意table-cell的特性有点像inline-block
>> - 父元素需要设置计算值为table-cell，vertical-align: middle，高度不接受百分比，只接受数值，margin设置无效，响应padding设置
>> - 不同于水平居中，子元素不必一定是inline-block，高度会自动适应
>> - IE6 IE7无效
```html
                // main.html
                <div class="contain">
                    <div class="centerBlock">我是居中的块级元素</div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    display: table-cell;
                    height: 400px;
                    vertical-align: middle;
                    background: #000;
                }

                .centerBlock {
                    background: #fff;
                } 
```
            
### 6.3 水平垂直居中

        
#### 1) 绝对定位auto方案
> - 需要已知长度和高度
```html
                // main.html
                <div class="contain">
                    <div class="centerBlock">我是居中的块级元素</div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    position: relative;
                    width: 100px;
                    height: 100px;
                    background: #000;
                }

                .centerBlock {
                    display: inline-block;
                    position: absolute;
                    left: 0;
                    right: 0;
                    top: 0;
                    bottom: 0;
                    width: 40px;
                    height: 40px;
                    margin: auto;
                    background: #fff;
                }
```

#### 2) 绝对定位translate方案
> - 不需要已知长度和高度
```html
                // main.html
                <div class="contain">
                    <div class="centerBlock">我是居中的块级元素</div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    position: relative;
                    width: 100px;
                    height: 100px;
                    background: #000;
                }

                .centerBlock {
                    display: inline-block;
                    position: absolute;
                    top: 50%;
                    left: 50%;
                    transform: translate(-50%, -50%);
                    background: #fff;
                }
```

#### 3) inline-block方案
> - vertical-align and text-align
> - 如果子元素内部有多行文字，且没有设vertical-align: middle;那么竖直方向上第一行会往上跳，居中对齐的是最后一行中间。
> - 会存在幽灵空白节点的问题，详细看[6.5 消除幽灵空格](#6.5)
```html
                // main.html
                <div class="contain">
                    <div class="centerBlock">我是居中的块级元素</div>
                </div>

                // main.css
                .contain {
                    width: 100px;
                    line-height: 100px;
                    text-align: center;
                    background: #000;
                }

                .centerBlock {
                    display: inline-block;
                    line-height: 1;
                    vertical-align: middle;
                    background: #fff;
                }
```

#### 4) table-cell方案
> - 不需要理会行高的问题，只用text-align和vertical-align就能保证
> - 自身元素计算值设为inline-block
```html
                // main.html
                <div class="contain">
                    <div class="centerBlock">我是居中的块级元素</div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    display: table-cell;
                    width: 100px;
                    height: 100px;
                    text-align: center;
                    vertical-align: middle;
                    background: #000;
                }

                .centerBlock {
                    display: inline-block;
                    background: #fff;
                }
```
        
### 6.4 清除浮动

        
#### 1) 原因
> - 对于块级元素，当其高度没有被指定的时候，其高度由内部的存在于文档流中的元素的高度所决定。但是，问题来了，如果内部的某个元素由于浮动或者绝对定位等原因脱离了文档流，但么块级元素的高度可能会发生变化(变小)，严重的可能会引起高度坍塌。
> - [浮动元素会脱离文档流但不会脱离文本流，因而会造成文本环绕效果，而这也是浮动的本意。](https://segmentfault.com/a/1190000007030144)
> - [浮动元素的外边距不会合并](https://segmentfault.com/a/1190000007030144)
> - [浮动非替换元素时必须设定宽度](https://segmentfault.com/a/1190000007030144)
> - [浮动元素会脱离文档流但不会脱离文本流，因而会造成文本环绕效果，而这也是浮动的本意。](https://segmentfault.com/a/1190000007030144)
> - [不管是块级元素还是内联元素，一旦浮动就会变成行内块元素（即display: inline-block;）](https://segmentfault.com/a/1190000007030144)
> - [如果浮动元素应用了负外边距而导致其与相邻元素重叠，分两种情况：](https://segmentfault.com/a/1190000007030144)
>> - [行内框与一个浮动元素重叠时，其边框、背景和内容都在该浮动元素之上显示](https://segmentfault.com/a/1190000007030144)
>> - [块框与一个浮动元素重叠时，其边框和背景都在该浮动元素之下显示，而内容在浮动元素之上显示](https://segmentfault.com/a/1190000007030144)
#### 2) 解决办法
> - BFC block-formatting context 块级格式化上下文
> - BFC有一个特性：内部元素无论怎么'折腾'，都不会干扰外部的元素。这意味着不会发生margin重叠，也不会发生高度坍塌。
>> - html根元素
>> - float的值不为none；
>> - position的值不为relative和static
>> - overflow为auto，scroll，hidden
>> - display的值为table-cell、table-caption和inline-block
>>>>> ![图6-1 清除浮动](https://github.com/hblvsjtu/FET/blob/master/picture/%E5%9B%BE6-1%20%E6%B8%85%E9%99%A4%E6%B5%AE%E5%8A%A8.png?raw=true)
```html
                // main.html
                <div class="contain">
                    <div class="floatBlock">我是正常元素</div>
                </div>

                <div class="contain">
                    <div class="floatBlock">我是浮动元素造成了坍塌</div>
                </div>

                <div class="contain">
                    <div class="floatBlock">我是浮动元素经过了overflow：hidden修复</div>
                </div>

                <div class="contain">
                    <div class="floatBlock">我是浮动元素经过了父元素inline-block修复</div>
                </div>

                <div class="contain">
                    <div class="floatBlock">我是浮动元素经过了父元素clear:both修复</div>
                </div>

                <div class="contain">
                    <div class="floatBlock">我是浮动元素经过了父元素absolute修复</div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                .contain {
                    width: 400px;
                    background: #000;
                }

                .floatBlock {
                    display: inline-block;
                    width: 200px;
                    margin: 10px;
                    height: 50px;
                    background: #fff;
                }

                .contain:nth-child(2) .floatBlock,
                .contain:nth-child(3) .floatBlock,
                .contain:nth-child(4) .floatBlock,
                .contain:nth-child(5) .floatBlock,
                .contain:nth-child(6) .floatBlock {
                    float: left;
                }

                .contain:nth-child(3){
                    overflow: hidden;
                }

                .contain:nth-child(4) {
                    display: inline-block;
                }

                .contain:nth-child(5) {
                    zoom: 1;
                }
                .contain:nth-child(5)::after {
                    content: '';
                    display: block;
                    height: 0;
                    visibility: hidden;
                    clear: both;
                }

                .contain:nth-child(6) {
                    position: absolute;
                }
```
        
### 6.5 幽灵空白节点

        
#### 1) W3C规范
> - line boxes are created as needed to hold inline-level content within an inline formatting context. Line boxes that contain no text, no preserved white space, no inline elements with non-zero margins, padding, or borders, and no other in-flow content (such as images, inline blocks or inline tables), and do not end with a preserved newline must be treated as zero-height line boxes for the purposes of determining the positions of any elements inside of them, and must be treated as not existing for any other purpose.
> - 如果一个line box里没有文字、保留的空格、非0的margin或padding或border的inline元素、或其他in-flow内容（比如图片、inline-block或inline-table元素），且不以保留的换行符结束的话，就会被视作高度为0的line box。但是一旦出现以上任意一种情况，就会出现幽灵空白节点。说白点，行框里只要有in-flow（图片、inline-block或inline-table元素），就会出现幽灵空白节点
> - 在一个行框内，对于一个inline-block，如果内部没有文字，或者overflow不是visible，那么他的基线将在于margin底部，如果里面有文字，将于最后一行文字的基线对齐
#### 2) 如何消除呢？
> - 设置父元素font-size为0，然后再把子元素的font-size恢复
        
### 6.6 三列布局

        
#### 1) 双飞翼布局
> - 两侧宽度固定，中间宽度自适应
> - 中间的dom优先渲染
> - 允许三列中任意一列成为最高列
> - 额外使用了一个div标签，该div是用来取得内层center的宽度了，避免计算calc(100%-350px)
> - margin-left: -100%; //使得左栏放到上一行的最左边
> - margin-left: -右栏宽度; //使得右栏放到上一行的最右边
> - 为了避免中间栏被挤掉，需要设置body的最小宽度
```html
                // main.html
                <div class="container column">
                    <div class="center"></div>
                </div>
                <div class="left column"></div>
                <div class="right column"></div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                body {
                    min-width: 500px;
                }

                .column {
                  float: left;
                  height: 100px;
                }

                .container {
                  width: 100%;
                }

                .container .center {
                  height: 100%;
                  margin-left: 200px;
                  margin-right: 150px;
                  background: red;
                }

                .left {
                  width: 200px;
                  margin-left: -100%;
                  background: yellow; 
                }

                .right {
                  width: 150px;
                  margin-left: -150px;
                  background: green; 
                }
```

> - 不用div包裹内部center的版本 目前需要计算计算calc(100%-350px)，calc()支持到IE9。
```html
                // main.html
                <div class="center column"></div>
                <div class="left column"></div>
                <div class="right column"></div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                body {
                    min-width: 350px; // 200px + 150px
                }

                .column {
                    float: left;
                    height: 100px;
                }

                .center {
                    width: calc(100% - 200px - 150px);
                    margin-left: 200px;
                    margin-right: 150px;
                    background: red;
                }

                .left {
                    width: 200px;
                    margin-left: -100%;
                    background: yellow; 
                }

                .right {
                    width: 150px;
                    margin-left: -150px;
                    background: green; 
                }
```

#### 2) 圣杯布局
> - 多一个div作为container
> - container的左右padding为左右栏留出空位
> - 左右栏使用relative作平移补偿
```html
                // main.html
                <div class="container">
                    <div class="center column"></div>
                    <div class="left column"></div>
                    <div class="right column"></div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */
                 
                body {
                    min-width: 550px; // 200px+150px+200px
                }

                .container {
                    padding-left: 200px;
                    padding-right: 150px;
                    height: 100px;
                }

                .column {
                    float: left;
                    height: 100%;
                }

                .center {
                    width: 100%;
                    background: red;
                }

                .left {
                    position: relative;
                    left: -200px;
                    width: 200px;
                    margin-left: -100%;
                    background: yellow; 
                }

                .right {
                    position: relative;
                    right: -150px;
                    width: 150px;
                    margin-left: -150px;
                    background: green; 
                }
```

#### 3) 简单float布局
> - 左右分别来一个float，中间用margin撑开
> - center只能放在下面，否则会挤掉left和right
> - 缺点：center最后才渲染，而且center的文字流会收到left和right的影响
```html
                // main.html
                <div class="left"></div>
                <div class="right"></div>
                <div class="center"></div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */

                body {
                    min-width: 350px;
                }

                .center {
                    height: 100px;
                    margin-left: 200px;
                    margin-right: 150px;
                    background: red;
                }

                .left {
                    float: left;
                    width: 200px;
                    height: 100px;
                    background: yellow; 
                }

                .right {
                    float: right;
                    width: 150px;
                    height: 100px;
                    background: green; 
                }
```

#### 4) 绝对float布局
> 多一个div作为包裹
> 简单易用，兼容性好
> 中间最先出
```html
                // main.html
                <div class="container">
                    <div class="center"></div>
                    <div class="left"></div>
                    <div class="right"></div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */

                body {
                    min-width: 350px;
                }

                .container {
                    position: relative;
                    height: 100px;
                    overflow: hidden;
                }

                .center {
                    position: absolute;
                    left: 200px;
                    right: 150px;
                    top: 0;
                    bottom: 0;
                    background: red;
                }

                .left {
                    float: left;
                    width: 200px;
                    height: 100px;
                    background: yellow; 
                }

                .right {
                    float: right;
                    width: 150px;
                    height: 100px;
                    background: green; 
                }
```

#### 5) 绝对布局
> 多一个div作为包裹
> 简单易用，兼容性好
> 中间最先出
```html
                // main.html
                <div class="container">
                    <div class="center"></div>
                    <div class="left"></div>
                    <div class="right"></div>
                </div>

                // main.css
                @charset "UTF-8";
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-07-31
                 * @version $0.0.1$
                 */

                body {
                    min-width: 350px;
                }

                .container {
                    position: relative;
                    height: 100px;
                }

                .center {
                    position: absolute;
                    left: 200px;
                    right: 150px;
                    top: 0;
                    bottom: 0;
                    background: red;
                }

                .left {
                    position: absolute;
                    left: 0;
                    top: 0;
                    bottom: 0;
                    float: left;
                    width: 200px;
                    background: yellow; 
                }

                .right {
                    position: absolute;
                    right: 0;
                    top: 0;
                    bottom: 0;
                    width: 150px;
                    background: green; 
                }
```

### 6.7 弹性布局

      
#### 1) 容器
> - display: flex;    // 将块级元素设置为容器
> - display: inline-flex    // 将行内元素设置为容器
> - 当元素设置成弹性容器后，它的所有子元素变成弹性项目此时项目的float/clear/vertical-align属性会失效
#### 2) 主轴方向：flex-direction:
> - row，默认值，主轴是x轴，主轴起点是左端
> - row-reverse,  主轴是x轴，主轴起点是右端
> - column，主轴是y轴，主轴起点在顶部
> - column-reverse,主轴是y轴，主轴起点在底部
#### 3) 换行显示：flex-wrap
> - nowrap 默认值，空间不够时，也不换行，项目自动缩小
> - wrap 空间不够就换行
> - wrap-reverse 换行，并反转
#### 4) flex-flow
> - flex-direction + flex-wrap
#### 5) 定义项目在主轴上的对齐方式：justify-content
> - flex-start,默认值，以主轴起点对齐
> - flex-end，以主轴终点对齐
> - center  在主轴上居中对齐
> - space-between 两端对齐，两端无空白
> - space-around 每个间距大小相同，两边会留白
#### 6) 定义项目在交叉轴上的对齐方式：align-items
> - flex-start 交叉轴起点对齐
> - flex-end 交叉轴终点对齐
> - center 交叉轴居中对齐
> - baseline 交叉轴基线对齐，就是交叉轴起点
> - stretch 前提，项目不写高。占满交叉轴上所有的空间
#### 7) 项目中的属性
> - order 定义项目排列顺序，值越小，越靠近起点，默认值为0
> - flex-grow 定义项目的放大比例 取值：无单位整数，默认值0，不放大
> - flex-shrink 定义项目缩小的比例，容器空间不足时，项目该如何缩小。默认值为1。 取值为0，不缩小。取值越大，缩小越快。
> - flex-basis 主轴存在剩余空间时，分配给此项目多少空间，默认auto即本身宽度
> - flex: 默认值是 0 1 auto
#### 7) align-self 
> - 子项目自身的交叉轴对齐方式，会覆盖容器的align-item属性
#### 8) flex-grow和flex-shrink相关计算公式
> - 子元素空间 < 父容器
                
                父容器剩余空间 = 父容器宽度 - 子元素宽度之和
                增长单位 = 父容器剩余空间 / 各子元素flex-grow之和
                子元素实际宽度 = (flex-basis) + 增长单位 * (flex-grow)
> - 子元素空间 > 父容器
                
                子元素溢出的宽度 = 子元素的宽度之和 - 子元素宽度之和
                收缩单位 = 子元素溢出的宽度 / 各子元素flex_shrink之和
                计算的子元素的宽度 = (flex-basis) - 收缩单位*(flex-shrink)
#### 9) 手写一个圣杯布局
> - 包括header,nav,main,aside,footer
```html
        // mian.html
        <header>header</header>
        <div class="container">
            <main>main</main>
            <nav>nav</nav>
            <aside>aside</aside>
        </div>
        <footer>footer</footer>


        // mian.css
        @charset "UTF-8";
        /**
         * 
         * @authors ${冰红茶} (${hblvsjtu@163.com})
         * @date    2019-07-31
         * @version $0.0.1$
         */

        body {
            display: flex;
            flex-flow: column wrap; 
            min-width: 350px;
            min-height: 500px;
            height: 100%;
        }

        header,
        footer {
            display: flex;
            justify-content: center;
            align-items: center;
            flex: 0 0 100px;
            background: gray;
        }

        header {
            order: 1;
        }

        footer {
            order: 3;
        }

        .container {
            display: flex;
            flex-flow: row nowrap;
            order: 2;
            flex: 1 1 auto;
        }

        .container main {
            order: 2;
            flex: 1 1 auto;
            background: red;
        }

        .container nav {
            order: 1;
            flex: 0 0 200px;
            background: yellow;
        }

        .container aside {
            order: 3;
            flex: 0 0 150px;
            background: green;
        }

        .container main,
        .container nav,
        .container aside {
            display: flex;
            justify-content: center;
            align-items: center;
        }
```

>>>>>> ![图6-2 flex圣杯布局](https://github.com/hblvsjtu/FET/blob/master/picture/%E5%9B%BE6-2%20flex%E5%9C%A3%E6%9D%AF%E5%B8%83%E5%B1%80.png?raw=true)

### 6.8 响应式布局

        
#### 1) null
> -
        

### 6.9 变形动画

        
#### 1) 二维动画
> - 引自[落霞与孤鹜齐飞](https://segmentfault.com/a/1190000015236871)
```html 
                transform: translate(x, y); 沿着 X 和 Y 轴移动元素。
                transform: translate(100px, 100px);

                transform: rotate(angle); 旋转元素。
                transform: rotate(45deg);

                transform: scale(x, y); 倍数改变元素的宽度和高度。
                transform: scale(2, 3);

                transform: skew(x, y); 沿着 X 和 Y 轴倾斜。
                transform: skew(45deg, -45deg);

                transform-origin: x y; 旋转的基点位置（默认center center）。
                transform-origin: right bottom;

                transform: translateX(45px) rotate(45deg); 合并简写
```

#### 2) 三维动画
> - 引自[落霞与孤鹜齐飞](https://segmentfault.com/a/1190000015236871)
> - preserve-3d：保证所有子元素都处于同一个三维空间
> - perspective定义摄像机（也就是作为观众的我们）到屏幕的距离
> - perspective-origin定义摄像机观察到的画面中的灭点（vanishing point）的位置
```html
                transform-style: preserve-3d;
                perspective: 24px;  设置元素被查看位置的视图  
                perspective-oragin: center center; 改变视点的位置

                transform: translate3d();
                transform: translateX();
                transform: translateY();
                transform: translateZ();

                transform: rotate3d();
                transform: rotateX();
                transform: rotateY();
                transform: rotateZ();

                transform: scale3d();
                transform: scaleX();
                transform: scaleY();
                transform: scaleZ();
```

### 6.10 补间动画

        
#### 1) null
> - 

        
------      
        
## 九、浏览器篇
### 9.3 defer和async的区别

        
#### 1) 相同点
> - 都用在script的异步脚本加载中，
#### 2) 不同点
> - 脚本的执行时间和执行顺序
> - async的脚本是看那个脚本最先下载完成先执行，跟写在HTML上的顺序是不同的
> - defer实在DOM解析完成后，DOMContentLoaded 事件触发之前完成的，一般是按照写在HTML上的顺序执行，但是实际体验下来这个顺序不能保证
>>>>>> ![图9-1 async和defer的区别](https://github.com/hblvsjtu/FET/blob/master/picture/%E5%9B%BE9-1%20async%E5%92%8Cdefer%E7%9A%84%E5%8C%BA%E5%88%AB.png?raw=true)
### 9.5 浏览器性能和计时器

        
#### 1) 高消耗的样式
> - box-shadows
> - border-radius
> - transparency
> - transforms
> - CSS filters（性能杀手）
#### 2) 减少重排Reflow的经验
> - 不要逐条修改CSS样式，最好预先写成class，再使用dom.classList.add()
> - 离线修改DOM: 先把 DOM 给 display:none, 再把它还原；
> - 为动画的元素使用绝对定位 absolute / fixed
> - 不要使用 table 布局
#### 3) 优化动画性能
> - GPU （Graphics Processing Unit） 是图像处理器，再处理图像上更加有效率
> - GPU加速可以不仅应用于3D，而且也可以应用于2D，常用的场合：Canvas2D，布局合成（Layout Compositing）, CSS3转换（transitions），CSS3 3D变换（transforms），WebGL和视频(video)。
> - 所以如果需要提升transforms的性能，可以强制为它开启3D，如transform: translate3d(10px, 10px, 0);
> - 或者使用"transform:translateZ(0);
```css 
                .cube { 
                    -webkit-transform: translateZ(0); 
                    -moz-transform: translateZ(0); 
                    -ms-transform: translateZ(0); 
                    -o-transform: translateZ(0); 
                    transform: translateZ(0);
                }
```
> - 在 Chrome 和 Safari中， 以下声明可以解决转换或动画可能会看到闪烁的效果
```css
                .cube { 
                    -webkit-backface-visibility: hidden;
                    -moz-backface-visibility: hidden;
                    -ms-backface-visibility: hidden;
                    backface-visibility: hidden;
                    -webkit-perspective: 1000;
                    -moz-perspective: 1000;
                    -ms-perspective: 1000;
                    perspective: 1000;
                }
```
> - 那问题来了，为什么开启3D来打开GPU加速可以优化动画性能呢？因为浏览器DOM渲染需要经过重排和重绘两个过程，其中重排的消耗最大。那问题就来到如果减少重排和重绘，甚至避免重排和重绘，借此提高动画的性能。动画是有帧组成的连续画面，开启GPU加速，即是GPU计算'层'，或者叫「纹理」，实际上是是DOM快照，通过已知变换矩阵来修改'层'，实质上是位图，来避免DOM的重排和重绘。
> - 那问题又来了：什么情况下会触发层的创建呢？引自[chokcoco的回答](https://github.com/ccforward/cc/issues/42)
>> - 3D 或透视变换(perspective、transform) CSS 属性
>> - 使用加速视频解码的 元素
>> - 拥有 3D (WebGL) 上下文或加速的 2D 上下文的 元素
>> - 混合插件(如 Flash)
>> - 对自己的 opacity 做 CSS 动画或使用一个动画变换的元素
>> - 拥有加速 CSS 过滤器的元素， 如：
```css      
                filter: brightness(50%); // 明度滤镜
                filter: saturate(1000%); // 饱和度滤镜
                filter: blur(5px); // 模糊滤镜
                filter: hue-rotate(45deg); // 色相反转滤镜
                filter: invert(100%); // 颜色反转滤镜
                filter: contrast(25%); // 对比度滤镜
                filter: drop-shadow(5px 5px 5px red); //阴影滤镜 第一个值是X方向上的位移，第二个值是Y轴方向上的位移，第三个值是模糊的大小，第四个值是模糊的颜色。
```
>> - 元素有一个包含复合层的后代节点，换句话说，就是一个元素拥有一个子元素，该子元素在自己的层里)
>> - 元素有一个 z-index 较低且包含一个复合层的兄弟元素(换句话说就是该元素在复合层上面渲染
            
------      
        
<h2 id='10'>十、V8引擎篇
### 10.0 事件循环

        
#### 1) 主线程
> - JS异步单线程里面的单线程指的是就是主线程，或者平常所说的『main』函数
#### 2) 任务队列(Macrotasks)
> - 当主线程在运作的时候，异步方法在指定的事件发生后，就会保存到一个队列中；当主线程在空闲时的时候，系统将会遍历该队列里面的方法并一一顺序执行。此队列就是'任务队列'。
> - 比如dom事件、setTimeout、setInterval、ajax事件
#### 3) 微任务队列(Microtasks)
> - 就是在主线程和任务队列隔着的一层队列，当主线程空闲时，先遍历微任务队列并把里面的任务一一顺序执行，再遍历任务队列并一一顺序执行里面的方法。
> - 如promise、process.nextTicks、MutationObserver
