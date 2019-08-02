# FET

## 作者：冰红茶  
    
------    
    
平常在生活中或者工作中不断的学习前端知识，记录和分享吾之所见吾之所悟^_ ^

## [目录](https://github.com/hblvsjtu/FrontEndTechonology/blob/master/README.md)
## [五、js和html效果篇](#5)
### [5.1 获取元素样式/位置/尺寸](#5.1)
### [5.2 拖拽](#5.2)
### [5.3 图片懒加载](#5.3)
### [5.4 轮播](#5.4)
### [5.5 滑动](#5.5)
### [5.6 级联](#5.6)
### [5.7 图片剪裁](#5.7)
### [5.8 图片压缩](#5.8)
### [5.9 Tab](#5.9)

        
------      
        
<h2 id='5'>五、js和html效果篇</h2>
<h3 id='5.1'>5.1 获取元素样式/位置/尺寸</h3>

        
#### 1) 样式
> - element.getAttribute()方法 只能获取内联样式的内容
                
                var btn=element.getAttribute('style');
> - document.styleSheets 获取内嵌样式表或外联样式表，返回值是一个数组
                
                var styleSheetList = document.styleSheets;
                var styleSheet = styleSheetList[0];
                var cssRuleList = styleSheet.rules;
                var cssStyleRule = cssRuleList[0];
                var styleDecl = cssStyleRule.style;
                console.log(styleDecl.width);
> - class属性的操作
>> - className
>> - classList 兼容性问题。如果该类名不存在则会在元素中添加类名，并返回 true。 第二个是可选参数，是个布尔值用于设置元素是否强制添加或移除类，不管该类名是否存在.注意： Internet Explorer 或 Opera 12 及其更早版本不支持第二个参数。
                
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

>> - 自定义类解决兼容性问题，可以兼容IE7
                
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
> - 获取实时计算的样式 getComputedStyle
>> - 只读的，不能写。
>> - 获取的是最终应用在元素上的所有CSS属性对象
>> - currentStyle不能读取伪类，但是getComputedStyle可以
>> - currentStyle是IE自娱自乐的玩意
>> - 在访问例如background-color类似格式的css属性时
                
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

#### 2) 位置
> - 元素的位置
>> - getClientRects 返回一个数组，但是该数组只有一个元素，而且是一个对象元素
>> - getBoundingClientRect用于获取元素相对与浏览器视口的位置，它是一个对象
>> - getClientRects和getClientRects都是元素边内界边缘相对于浏览器视口的距离
>> - 想要获取元素边内界边缘相对于文档顶部的距离，需要用到offsetTop,offsetLeft和offsetParent
                
                getBoundingClientRect： {
                        top: '元素顶部相对于视口顶部的距离',
                        bottom: '元素底部相对于视口顶部的距离',
                        left: '元素左边相对于视口左边的距离',
                        right: '元素右边相对于视口左边的距离',
                        height: '元素高度',
                        width: '元素宽度'
                        x: 8,
                        y: 8,
                    }
>> - 兼容性写法 因为IE没有height和width
                
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
>> - 一个例子
                
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

<h3 id='5.2'>5.2 拖拽</h3>

        
#### 1) 行内元素
> - 
<h3 id='5.3'>5.3 图片懒加载</h3>

        
#### 1) 行内元素
> - 
<h3 id='5.4'>5.4 轮播</h3>

        
#### 1) 行内元素
> - 
<h3 id='5.5'>5.5 滑动</h3>

        
#### 1) 行内元素
> - 
<h3 id='5.6'>5.6 级联</h3>

        
#### 1) 行内元素
> - 
<h3 id='5.7'>5.7 图片剪裁</h3>

        
#### 1) 行内元素
> - 
<h3 id='5.8'>5.8 图片压缩</h3>

        
#### 1) 行内元素
> - 
<h3 id='5.9'>5.9 Tab</h3>

        
#### 1) 行内元素
> - 
