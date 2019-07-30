# FET

## 作者：冰红茶  
## 参考书籍：[JavaScript框架设计] 第二版 作者：司徒正美
    
------    
    
平常在生活中或者工作中不断的学习前端知识，记录和分享吾之所见吾之所悟^_ ^

## 目录
## [一、类型判断篇](#1)
### [1.1 基本数据类型](#1.1)
### [1.2 对象类型系统](#1.2)
### [1.3 平台](#1.3)
## [二、常用方法篇](#2)
### [2.1 拷贝](#2.1)
### [2.2 类数组判断与转化](#2.2)
### [2.3 数组去重](#2.3)
### [2.4 数组洗牌](#2.4)
### [2.5 数组排序](#2.5)
### [2.6 最大重复子序列](#2.6)
### [2.7 最大重复子数组](#2.7)
### [2.8 ajax封装](#2.8)
### [2.9 String.format](#2.9)
## [三、原理实现篇](#3)
### [3.1 call/apply/bind](#3.1)
### [3.2 Deferred和Promise](#3.2)
### [3.3 async/await](#3.3)
### [3.4 观察者模式](#3.4)
### [3.5 防抖动和截流](#3.5)
### [3.6 类的继承](#3.6)
### [3.7 new](#3.7)
### [3.8 Object.create()](#3.8)
### [3.9 Object.keys/Object.values/Object.entries](#3.9)
### [3.10 setTimeout 与 setInterval](#3.10)
### [3.11 跨域](#3.11)
### [3.12 函数柯里化](#3.12)
### [3.13 高阶函数](#3.13)
## [四、正则表达式篇](#4)
### [4.1 断言](#4.1)
### [4.2 分组](#4.2)
### [4.3 非贪婪](#4.3)
### [4.4 电话号码/身份证/网址/邮箱](#4.4)
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
                function isObject(o) {
                    return '[object Object]' === {}.toString.call(o); 
                }
#### 2) 函数
> - 
                
                function isFunction(o) {
                    return '[object Function]' === {}.toString.call(o); 
                }
#### 3) 正则表达式
> - 
                
                function isRegExp(o) {
                    return '[object RegExp]' === {}.toString.call(o); 
                }
#### 4) 日期
> - 
                
                function isDate(o) {
                    return '[object Date]' === {}.toString.call(o); 
                }
#### 5) 数组
> - 
                
                function isArray(o) {
                    return '[object Array]' === {}.toString.call(o); 
                }
#### 6) 全类型判断
                
                function type(o) {
                    if(o === null) return "null";
                    else if(o !== o) return "NaN";
                    else if(o === void 0) return "undefined";
                    else {
                        let type = {}.toString.call(o).slice(8, -1);
                        return type ? type : '它不是基本类型'
                    }
                }


<h3 id='1.3'>1.3 平台</h3>
        
#### 1) window
> - 需要区分不同的平台
> - IE6、7、8利用window == document为真 但是document == window为假的神奇特性
> - 标准浏览器及IE9,IE10等使用鸭子辩型的方法
                
                // IE6、7、8
                function isWindow(obj) {
                    return obj == obj.document && obj.document != obj;
                }
                // 标准浏览器及IE9,IE10
                function isWindow(obj) {
                    return /^\[object (Window|DOMWindow|global)/.test({}.toString.call(obj));
                }
#### 2）浏览器
> - 判断浏览器类型
> - 利用navigator.userAgent来判断
> - 要把browsers数组里面的子项按照顺序来放，因为有时候userAgent里面会同时出现两种或以上的子项，当Safari出现的时候一般在userAgent的最后面，而"Chrome"次之，所以需要把他们放在前面先进行遍历
                
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


------      
        
<h2 id='2'>二、常用方法篇</h2>
<h3 id='2.1'>2.1 拷贝</h3>

        
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
                
<h3 id='2.2'>2.2 类数组判断与转化</h3>

        
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

                    
<h3 id='2.4'>2.4 数组乱序</h3>
        
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


                        
<h3 id='2.8'>2.8 ajax封装</h3>
        
        
#### 1) 功能
> - 
> - 

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
#### 2) 一个更加简介的办法：利用replace()
> - 第二个参数可以是函数，将每匹配到的一组分组就执行一次
                
                String.prototype.iFormat = function(transfer)   {
                    return this.replace(/\$\{.+?\}/g, function(group){
                        return transfer[group.replace(/(^\$\{)|(\}$)/g, '')];
                    })
                }

                let str = "${a}ads${a}sad${b}as${c}zx${c}";
                str.iFormat({a: ' I ', b: ' love ', c: ' you '});
                // " I ads I sad love as you zx you "


<h2 id='3'>三、原理实现篇</h2>
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

<h3 id='3.2'>3.2 Deferred和Promise</h3>

        
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
#### 2) Promise(第一次自己写的)
> - Promise是Deferred/promise的混合版
> - Promise既作触发器又做储存器
> - 需要在resolve和reject上包装，已达到窃听的效果
> - 实现resolve和reject原型方法
> - 如果返回值是空类型，则正常返回this作链式调用，如果返回值非空也非Promise类型，则作为参数传到下一个then，可惜这个我实现不了
                
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

#### 3) Promise(看了别人代码后自己写的)
> - 为了支持同步的Promise，采用异步调用_resolve和_reject
> - then方法比较复杂，首先返回的是一个promise，然后根据不同的返回值类型进行进一步处理
> - function(cal) {try {resolve(val) or reject(val)} catch(e) {reject(e)}}
> - catch是唯一没有可能返回promise的函数
> - resolve和reject方法就是返回一个仅有resolve或者reject方法的promise，同时resolve方法将判断参数的类型，如果参数是非promise类型，将会把它包装成promise类型
> - all方法是返回一个promise，循环得到结果放到一个数组中，由于每个子项执行的时间不一致，只能新建计数器来统计then执行的次数，当计数器等于all的数组参数个数的时候才进行resolve的统一处理结果数组
> - race方法是返回一个promise，遍历所有的promise数组，不需要搜集结果
                
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

                
                        
<h3 id='3.4'>3.4 观察者模式</h3>
                
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

                        
<h3 id='3.5'>3.5 防抖动和截流</h3>
                
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

                        
<h3 id='3.6'>3.6 类的继承</h3>
                
#### 1) 属性拷贝
> - 这是最简单的，把父类的属性全都拷贝一份
#### 2) 原型式继承
> - 只能继承父构造函数的原型对象上的成员, 不能继承父构造函数的实例对象的成员
                
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

#### 3) 原型链继承
> - 将父类的公有和私有属性和公有方法都继承过来的
> - 优点：直接把父类的原型（浅）拷贝过来，简单易用
> - 缺点
>> - 新实例无法向父类构造函数传参
>> - 存在父类私有引用类型属性共享的问题
                
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
                
#### 4) 构造函数继承
> - 使用call继承父类的构造函数
> - 好处：可以得到父类的构造函数属性，向父类构造函数传参。
> - 坏处：无法得到父类的原型属性
                
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

#### 5) 组合继承
> - 原型链继承 + 构造函数继承
> - 解决了对象共享的问题，还能拿到父类的构造函数
> - 但是存在性能问题，因为父类有两次构造
                
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

#### 6) 组合继承优化1
> - 原型式继承 + 构造函数继承
> - 解决了对象共享的问题，还能拿到父类的构造函数
> - 不存在性能问题
> - 但是子类无法修改原型的constructor属性，因为一旦修改就会同时修改父类的constructor属性，换句话说无法辨别子类的构造函数是谁
                
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
                // Child.prototype.constructor = Child;
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

#### 7) 组合继承优化2
> - 目前来讲比较完美的方法
> - 使用寄生式组合继承
                
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
                Child.prototype = Object.create(Parent.prototype);
                Child.prototype.constructor = Child;

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

<h3 id='3.8'>3.8 Object.create()</h3>
                
#### 1) 参数
> - 第一个参数是原型对象
> - 第二个参数是属性特性：value, writable, enumberable, congigurable
                
                Object.prototype.myCreate = function(proto, properties) {
                    let f = function() {};
                    f.prototype = proto;
                    let o = new f();
                    if (typeof properties === 'object') {
                        Object.defineProperties(o, properties);
                    }
                    return o;
                }

<h3 id='3.9'>3.9 Object.keys/Object.values/Object.entries</h3>
                
#### 1) Object.keys
> - 返回对象的每个可枚举的自身属性键名组成的数组
                
                Object.prototype.myKeys = function(o) {
                    let arr = []
                    for(let key in o) {
                        if(o.hasOwnProperty(key)) arr.push(key);
                    }
                    return arr;
                }
#### 2) Object.values
> - 返回对象的每个可枚举的自身属性键值组成的数组
                
                Object.prototype.myValues = function(o) {
                    let arr = []
                    for(let key in o) {
                        if(o.hasOwnProperty(key)) arr.push(o[key]);
                    }
                    return arr;
                }
#### 2) Object.entrie
> - 返回对象的每个可枚举的自身属性键名和键值组成的数组
                Object.prototype.myEntries = function(o) {
                    let arr = []
                    for(let key in o) {
                        if(o.hasOwnProperty(key)) arr.push([key, o[key]]);
                    }
                    return arr;
                }

<h3 id='3.10'>3.10 setTimeout 与 setInterval</h3>
                
#### 1) 最短间隔时间
> - 如果回调时间大于间隔时间，浏览器才会执行，这也导致了真正的间隔时间比原来的大一点
> - 这个最短间隔时间该怎么测呢？可以利用在定时器内再嵌一个定时器
                
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

<h3 id='3.11'>3.11 跨域</h3>
                
#### 1) 通过document.domain跨域
> - 在相同的域名下建立文件
#### 2) 通过location.hash跨域
> - 但是如果内嵌的页面不同源的话是无法拿到iframe的document的
                
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
#### 3) 通过postMessage
> - 好像也做不了
> - 需要判断源origin，否则容易收到XXR攻击
                
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
#### 4) Jsonp
> - 只支持GET，不支持POST请求
> - 它只支持跨域HTTP请求这种情况，不能解决不同域的两个页面之间如何进行JavaScript调用的问题。
> - 支持老版本的浏览器
            
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
#### 5) Access-Control-Allow-Origin
> - 存在兼容性的问题，不兼容老版本的浏览器
> - 服务器设置
                
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

<h3 id='3.12'>3.12 函数柯里化</h3>
                
#### 1) 定义
> - 一个函数接受一些参数后返回一个新的函数，这个新的函数继续接收剩余的参数
> - 比如：
                
                // 原函数
                function origin(a, b, c) {

                }

                // 柯里化
                function curry(a) {
                    return function(b, c) {

                    }
                }
#### 2) 两段不定参数版本
> - 
                
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

#### 3) 不定段不定参数版本
> - 无限累加器
> - points
>> - 改写函数的toSting()和valueOf()方法
>> - 返回的函数作为参数收集器
>> - 真正做处理方法是toSting()和valueOf()方法
                
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

                
<h3 id='3.13'>3.13 高阶函数</h3>
                
#### 1) 定义
> - 接受一个或多个函数作为输入
> - 输出一个函数
#### 2) 实现一个map函数
> - 挂靠在Array数组原型上
                
                Array.prototype.myMap = function(func) {
                    let l = this.length;
                    let temp = [];
                    for(let i = 0; i < l; i++) {
                        temp[i] = func(this[i], i, this);
                    }
                    return temp;
                }
#### 3) 实现一个forEach函数
> - 挂靠在Array数组原型上
                
                Array.prototype.myForEach = function(func) {
                    let l = this.length;
                    for(let i = 0; i < l; i++) {
                        func(this[i], i, this);
                    }
                }
#### 4) 实现一个reduce函数
> - 挂靠在Array数组原型上
                
                Array.prototype.myReduce = function(func, init) {
                    let l = this.length;
                    let result = init ? init : 0;
                    for(let i = 0; i < l; i++) {
                        result = func(result, this[i], init);
                    }
                    return result;
                }
#### 5) 实现一个filter函数
> - 挂靠在Array数组原型上               
                
                Array.prototype.myFilter = function(func) {
                    let l = this.length;
                    let arr = [];
                    while(l--) if(func(this[l])) arr.unshift(this[l]);
                    return arr;
                }

