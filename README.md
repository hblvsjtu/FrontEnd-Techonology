# FET

## 作者：冰红茶  
## 参考书籍：[JavaScript框架设计] 第二版 作者：司徒正美
    
------    
    
平常在生活中或者工作中不断的学习前端知识，记录和分享吾之所见吾之所悟^_ ^

## 目录
## [一、类型判断篇](#1)
### [1.1 字符串](#1.1)
### [1.2 数字](#1.2)
### [1.3 布尔](#1.3)
### [1.4 null](#1.4)
### [1.5 undefined](#1.5)
### [1.6 原生对象](#1.6)
### [1.7 日期](#1.7)
### [1.8 函数](#1.8)
### [1.9 正则表达式](#1.9)
### [1.10 平台](#1.10)
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
## [四、正则表达式篇](#4)
### [4.1 电话号码](#4.1)
### [4.2 身份证](#4.2)
### [4.3 网址](#4.3)
### [4.4 邮箱](#4.4)
## [五、js和html效果篇](#5)
### [5.1 拖拽](#5.1)
### [5.2 图片懒加载](#5.2)
### [5.3 轮播](#5.3)
### [5.4 滑动](#5.4)
### [5.5 级联](#5.5)
### [5.6 图片剪裁](#5.6)
### [5.7 Tab](#5.7)
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
        
<h2 id='2'>二、常用方法篇</h2>
<h3 id='2.1'>拷贝</h3>

        
#### 1) 数组浅拷贝
> - 使用
#### 2) 数组深拷贝
> - 
> - 
                
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
> - 是一个函数
> - 相当于字符串模板
> - 第一个参数是模板，第二个参数是识别模板变量的边界，后面的参数是模板的数据
> - 挂载到String上
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

>>>>>> ![图3-1 new原理]()
>>>>>> 





