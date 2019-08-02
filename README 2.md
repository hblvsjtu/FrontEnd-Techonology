# FET

## 作者：冰红茶  
    
------    
    
平常在生活中或者工作中不断的学习前端知识，记录和分享吾之所见吾之所悟^_ ^

## 目录
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
### [2.10 String.thousandSplit](#2.10)

        
------      
              
<h2 id='2'>二、常用方法篇</h2>
<h3 id='2.1'>2.1 拷贝</h3>

        
#### 1) 数组浅拷贝
> - Object.assign
> - 
#### 2) 数组深拷贝
> - 先对输入进行判断，是数组、对象还是其他
> - 然后如果是数组或者对象的时候进行遍历，子元素是数组或者对象的时候直接赋值，否则进行递归
                
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
                
<h3 id='2.2'>2.2 类数组判断与转化</h3>

        
#### 1) 判断
> - 是一个对象
> - 有length属性
> - length属性的值是一个非负有限整数
                
                /**
                 * 
                 * @authors ${冰红茶} (${hblvsjtu@163.com})
                 * @date    2019-08-01
                 * @version $Id$
                 */

                function isArrayLike(obj) {
                    return obj && (typeof obj === 'object') &&  (obj.length >= 0) &&  obj.length < 4294967296 && (obj.length === Math.floor(obj.length))
                }
#### 2) slice的内部实现
> - 返回一个数组
> - 循环赋值从0到length
                
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
#### 3) 转化
> - 利用slice方法 [].slice.call(a);
> - Array.from();
> - 手动转化
                
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

                    
<h3 id='2.4'>2.4 数组乱序</h3>
        
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
#### 2) 一个更加简介的办法：利用replace()
> - 第二个参数可以是函数，将每匹配到的一组分组就执行一次
                
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


<h3 id='2.10'>2.10 String.thousandSplit</h3>
           
#### 1) 功能
> - 西方的数字从右往左每三位加一个分隔符
#### 2) 实现
> - 需要零宽正向预言
> - $表示从右往左
> - ，不能放在第一位
> - 需要全局判断，因为不止匹配一个
            
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
