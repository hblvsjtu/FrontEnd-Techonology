# FET

## 作者：冰红茶  
## 参考书籍：[JavaScript框架设计] 第二版 作者：司徒正美
    
------    
    
平常在生活中或者工作中不断的学习前端知识，记录和分享吾之所见吾之所悟^_ ^

## 目录
## [一、类型判断篇](#1)
### [1.1 基本数据类型](#1.1)
### [1.2 对象类型系统](#1.2)
### [1.3 平台](#1.13)
## [二、常用方法篇](#2)
### [2.1 拷贝](#2.1)
### [2.2 类数组判断与转化](#2.2)
### [2.3 数组去重](#2.3)
### [2.4 数组随机抽样](#2.4)
### [2.5 数组排序](#2.5)
### [2.6 最大重复子序列](#2.6)
### [2.7 最大重复子数组](#2.7)
### [2.8 ajax封装](#2.8)
### [2.9 String.format](#2.9)
## [三、原理实现篇](#3)
### [3.1 call/apply/bind](#3.1)
### [3.2 promise](#3.2)
### [3.3 async/await](#3.3)
### [3.4 观察者模式](#3.4)
### [3.5 防抖动和截流](#3.5)
### [3.6 类](#3.6)
### [3.7 new](#3.7)
### [3.8 Object.create()](#3.8)
### [3.9 Object.keys/Object.values/Object.entries](#3.9)
### [3.10 Array.map/Array.forEach/Array.reduce/Array.slice/Array.splice](#3.10)
### [3.11 监听器类](#3.11)
## [四、正则表达式篇](#4)
### [4.1 电话号码](#4.1)
### [4.2 身份证](#4.2)
### [4.3 网址](#4.3)
### [4.4 邮箱](#4.4)
## [五、js和html效果篇](#5)
### [5.1 获取高度和宽度](#5.1)
### [5.2 拖拽](#5.2)
### [5.3 图片懒加载](#5.3)
### [5.4 轮播](#5.4)
### [5.5 滑动](#5.5)
### [5.6 级联](#5.6)
### [5.7 图片剪裁](#5.7)
### [5.8 图片压缩](#5.8)
### [5.9 Tab](#5.9)
## [六、CSS效果篇](#5)
### [6.1 水平居中](#6.1)
### [6.2 垂直居中](#6.2)
### [6.3 水平垂直居中](#6.3)
### [6.4 清除浮动](#6.4)
### [6.5 消除幽灵空格](#6.5)
### [6.6 三列布局](#6.6)
### [6.7 响应式布局](#6.7)
### [6.8 变形动画](#6.8)
### [6.9 补间动画](#6.9)

        
------      
        
<h2 id='1'>一、类型判断篇</h2>
<h3 id='1.1'>1.1 基本数字类型</h3>

        
#### 1) null
> - 直接跟v他自己比较即可
                
                function isNull(o) {
                    return o === null;
                }
#### 2) NaN
> - 因为它连跟它自己比较都不相等，可以用此特性进行判断
                
                function isNaN(o) {
                    return o !== o;
                }
#### 3) undefined
> - undefined它并不是一个保留词，他是全局对象的一个属性，这说明什么呢？说明它有可能会被改写。到了ES5被改成只读了，但是在局部作用域中还是会被改写，虽然在最新的chrome 75.0.3770.142中我并没有发现改写-.-||
> - 为什么是void 0? 因为根据MDN的解释：The void operator evaluates the given expression and then returns undefined. 无论你给他赋什么的值，都会返回undefined，而0应该是最简单的喽
                
                function isUndefined(o) {
                    return o === void 0;
                }
#### 4) number
> - 采用鸭子辩型
> - 因为如果纯粹使用typeof的话会把包装类也识别成对象；
                
                function isNumber(o) {
                    return '[object Number]' === {}.toString.call(o) && isFinite(o); 
                }
#### 5) boolean
> - 采用鸭子辩型
> - 因为如果纯粹使用typeof的话会把包装类也识别成对象；
                
                function isboolean(o) {
                    return '[object Boolean]' === {}.toString.call(o); 
                }

<h3 id='1.2'>1.2 对象类型系统</h3>

#### 1) object
> - 


<h3 id='1.2'>1.2 对象类型系统</h3>

#### 1) window
> - 
> - 
> -                           



------      
        
<h2 id='2'>二、常用方法篇</h2>
<h3 id='2.1'>拷贝</h3>

        
#### 1) 数组浅拷贝
> - Object.assign
> - 
#### 2) 数组深拷贝
> - 先对输入进行判断，是数组、对象还是其他
> - 然后如果是数组或者对象的时候进行遍历，子元素是数组或者对象的时候直接赋值，否则进行递归
                
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
                
<h3 id='2.2'>类数组判断与转化</h3>

        
#### 1) 判断
> - 是一个对象
> - 有length属性
> - length属性的值是一个非负有限整数
                
                function isArrayLike(obj) {
                    return obj && (typeof obj === 'object') &&  (obj.length >= 0) &&  obj.length < 4294967296 && (obj.length === Math.floor(obj.length))
                }
#### 2) slice的内部实现
> - 返回一个数组
> - 循环赋值从0到length
                
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
#### 3) 转化
> - 利用slice方法 [].slice.call(a);
> - Array.from();
> - 手动转化
                
                function transfer(obj) {
                    let arr = [];
                    let l = obj.length;
                    while(l > 0) arr[--l] = obj[l];
                    return arr;
                }


<h3 id='2.9'>2.9 String.format</h3>
        
        
#### 1) 功能
> - 是一个函数挂载到String的原型上
> - 相当于字符串模板
> - 参数是模板的数据
> - 分别用两个正则表达式切割关键词和非关键词，然后在进行拼接
                
                String.prototype.iFormat = function(data) {
                    let keyArray = this.match(/(?<=\$\{)\S+?(?=\})/g);
                    let strArray = this.split(/\$\{\S+?\}/g);
                    return strArray.map((item, index) => data[keyArray[index]] ? item + data[keyArray[index]] : item).join('');
                }

                let str = "${a}ads${a}sad${b}as${c}zx${c}";
                str.iFormat({a: ' I ', b: ' love ', c: ' you '}); //" I ads I sad love as you zx you "


<h2 id='1'>三、原理实现篇</h2>
<h3 id='3.1'>3.1 call/apply/bind</h3>

        
#### 1) call
> - 返回一个立即执行的函数
> - 该函数的作用域被绑定为第一个形参
> - 其他的形参作为原函数的参数
> - 模拟的方法被绑定在函数的原型上，方便调用
                
                Function.prototype.myCall = function(content) {
                    content.func = this; //转移this
                    let arr = [], l = arguments.length;
                    while(l > 0) arr[--l] = arguments[l];
                    arr.shift();
                    return this(...arr);
                }

                let a = function(num, num1) {
                    this.num = this.num ? this.num + num1 : num;
                    console.log(this.num);
                }

                let b = {num: 1};

                a.myCall(b, 2, 3);

                // 4

#### 2) apply
> - 根据call把参数改成数组输入的形式
                
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
#### 3) bind
> - 返回一个函数
> - 函数的作用域为bind的第一个参数
> - 如果bind的参数不足够原函数消化，剩余的参数可以在返回的函数中输入
> - 作为原型挂靠在Function上
                
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

                        
<h3 id='3.6'>3.6 防抖动和截流</h3>
                
#### 1) 相同点
> - 防止用户频繁的操作造成阻塞或者屏幕抖动，提升用户体验
> - 提升性能
#### 2) 不同点
> - 防抖动是发生在操作与操作之间的时间空隙，拉长操作之间的延迟时间
> - 截流是指在连续重复的操作中，保证每次的操作时间周期，一般比操作实际运行的时间要长
#### 3) 防抖动
> - 需要用到setTimeout
> - 用bounce对回调函数进行包装
> - 注意setTimeout和的作用域：内部延迟执行的代码中的this永远指向window，但是回调函数本身的this可以指向其他，所以setTimeout需要先在全局进行定义。
                
                let myTimer;
                let deBounce = function(delayTime, callback) {
                    clearTimeout(myTimer);
                    myTimer = setTimeout(function() {
                            if(callback) callback()
                            console.log('用户的操作。。。');
                        }, delayTime);
                }

                document.addEventListener('click', function() {
                    deBounce(3000);
                });
#### 4) 截流/频率控制
> - 需要比较实际运行时间长度和设定的周期时间
> - 立即执行，无需使用setTimeout
> - 如果实际运行时间长度 > 设定的周期时间, 则运行回调，并且把当前时间戳设为旧时间戳；
                
                let old = new Date();
                let throttle = function(cycleTime, callback) {
                    let now = new Date();
                    if (now - old > cycleTime) {
                        if (callback) callback();
                        old = now;
                    }
                }

                document.addEventListener('click', function() {
                    throttle(3000, function() {
                            console.log('i am working');
                        });
                });
#### 5) 防抖动和截流合并
> - 在截流里面把防抖动的函数写进去
                
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

<h3 id='3.7'>3.7 new</h3>
                
#### 1) 要点
> - 返回一个对象
> - 对象的原型属性等于函数的原型
> - 对象的属性需要函数去更换自身的作用域为对象的作用域获得
                
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

>>>>>> ![图3-1 new原理](https://github.com/hblvsjtu/FET/blob/master/picture/%E5%9B%BE3-1%20new%E5%8E%9F%E7%90%86.png?raw=true)

<h3 id='3.11'>3.11 监听器类</h3>
                
#### 1) 要点
> - 监听器listener：其实是一系列的函数
> - 监听器类型: type
> - 监听器注册表：
                
                let _registers = [
                                    {
                                        type: '',
                                        listener: ''
                                    },
                                    ...
                                ]
> - 监听器列表：
                
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
> - 建立一个类
>> - 原型变量:注册表和监听器列表
>> - 原型方法：添加/删除 某类型的监听器
                
                
#### 2) 代码
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





