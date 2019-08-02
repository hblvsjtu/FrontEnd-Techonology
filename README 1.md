# FET

## 作者：冰红茶  
    
------    
    
平常在生活中或者工作中不断的学习前端知识，记录和分享吾之所见吾之所悟^_ ^

## [目录](https://github.com/hblvsjtu/FrontEndTechonology/blob/master/README.md)
## [一、类型判断篇](#1)
### [1.1 基本数据类型](#1.1)
### [1.2 对象类型系统](#1.2)
### [1.3 平台](#1.3)


        
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


<h3 id='1.3'>1.3 平台</h3>
        
#### 1) window
> - 需要区分不同的平台
> - IE6、7、8利用window == document为真 但是document == window为假的神奇特性
> - 标准浏览器及IE9,IE10等使用鸭子辩型的方法
                
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
#### 2）浏览器
> - 判断浏览器类型
> - 利用navigator.userAgent来判断
> - 要把browsers数组里面的子项按照顺序来放，因为有时候userAgent里面会同时出现两种或以上的子项，当Safari出现的时候一般在userAgent的最后面，而"Chrome"次之，所以需要把他们放在前面先进行遍历
                
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
