# FET

## 作者：冰红茶  
    
------    
    
平常在生活中或者工作中不断的学习前端知识，记录和分享吾之所见吾之所悟^_ ^

## [目录](https://github.com/hblvsjtu/FrontEndTechonology/blob/master/README.md)
## [六、CSS效果篇](#6)
### [6.1 水平居中](#6.1)
### [6.2 垂直居中](#6.2)
### [6.3 水平垂直居中](#6.3)
### [6.4 清除浮动](#6.4)
### [6.5 消除幽灵空格](#6.5)
### [6.6 三列布局](#6.6)
### [6.7 弹性布局](#6.7)
### [6.8 响应式布局](#6.8)
### [6.9 变形动画](#6.9)
### [6.10 补间动画](#6.10)

        
------      
        
<h2 id='6'>六、CSS效果篇</h2>
<h3 id='6.1'>6.1 水平居中</h3>

        
#### 1) 行内元素
> - 父元素上text-align: center;
                
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
#### 2) 块级元素
> - 定宽居中
>> - 自身元素上margin: auto; 一定要写width;
                
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
> - inline-block不定宽居中
>> - 把块状元素的显示值设置为inline-block
>> - 然后使用行内元素的text-align: center;
                
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
> - 绝对定位不定宽居中
>> - 注意IE8及以下不支持transform，其他的也需要加后缀
                
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
> - table-cell不定宽居中
>> - 注意table-cell的特性有点像inline-block，需要设置width，而且不接受百分比，只接受数值，table-cell
>> - IE6 IE7无效
                
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


<h3 id='6.2'>6.2 垂直居中</h3>

        
#### 1) 行内元素
> - 父元素需要设置行高
> - 自身元素上设置vertical-align
                
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
#### 2) 块级元素
> - line-height不定高居中
>> - 父元素需要设置行高，高度将被行高顶起，相当于设了高度
>> - 子元素设置vertical-align: middle，这是因为子元素被设为inline-block后，其基线将于内部文字的中线重合
>> - 由于父元素的行高等于自身高度，而子元素的基线在内部文字的中线上，所以就变成竖直居中了
>> - 会存在幽灵空白节点的问题，详细看[6.5 消除幽灵空格](#6.5)
                
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

> - 绝对定位不定高居中
>> - 注意IE8及以下不支持transform，其他的也需要加后缀
>> - 父元素需要设置高度
                
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
> - table-cell不定高居中
>> - 注意table-cell的特性有点像inline-block
>> - 父元素需要设置计算值为table-cell，vertical-align: middle，高度不接受百分比，只接受数值，margin设置无效，响应padding设置
>> - 不同于水平居中，子元素不必一定是inline-block，高度会自动适应
>> - IE6 IE7无效
                
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

            
<h3 id='6.3'>6.3 水平垂直居中</h3>

        
#### 1) 绝对定位auto方案
> - 需要已知长度和高度
                
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

#### 2) 绝对定位translate方案
> - 不需要已知长度和高度
                
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

#### 3) inline-block方案
> - vertical-align and text-align
> - 如果子元素内部有多行文字，且没有设vertical-align: middle;那么竖直方向上第一行会往上跳，居中对齐的是最后一行中间。
> - 会存在幽灵空白节点的问题，详细看[6.5 消除幽灵空格](#6.5)
                
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

#### 4) table-cell方案
> - 不需要理会行高的问题，只用text-align和vertical-align就能保证
> - 自身元素计算值设为inline-block
                
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
     
        
<h3 id='6.4'>6.4 清除浮动</h3>

        
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

        
<h3 id='6.5'>6.5 幽灵空白节点</h3>

        
#### 1) W3C规范
> - line boxes are created as needed to hold inline-level content within an inline formatting context. Line boxes that contain no text, no preserved white space, no inline elements with non-zero margins, padding, or borders, and no other in-flow content (such as images, inline blocks or inline tables), and do not end with a preserved newline must be treated as zero-height line boxes for the purposes of determining the positions of any elements inside of them, and must be treated as not existing for any other purpose.
> - 如果一个line box里没有文字、保留的空格、非0的margin或padding或border的inline元素、或其他in-flow内容（比如图片、inline-block或inline-table元素），且不以保留的换行符结束的话，就会被视作高度为0的line box。但是一旦出现以上任意一种情况，就会出现幽灵空白节点。说白点，行框里只要有in-flow（图片、inline-block或inline-table元素），就会出现幽灵空白节点
> - 在一个行框内，对于一个inline-block，如果内部没有文字，或者overflow不是visible，那么他的基线将在于margin底部，如果里面有文字，将于最后一行文字的基线对齐
#### 2) 如何消除呢？
> - 设置父元素font-size为0，然后再把子元素的font-size恢复
        
<h3 id='6.6'>6.6 三列布局</h3>

        
#### 1) 双飞翼布局
> - 两侧宽度固定，中间宽度自适应
> - 中间的dom优先渲染
> - 允许三列中任意一列成为最高列
> - 额外使用了一个div标签，该div是用来取得内层center的宽度了，避免计算calc(100%-350px)
> - margin-left: -100%; //使得左栏放到上一行的最左边
> - margin-left: -右栏宽度; //使得右栏放到上一行的最右边
> - 为了避免中间栏被挤掉，需要设置body的最小宽度
                
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

> - 不用div包裹内部center的版本 目前需要计算计算calc(100%-350px)，calc()支持到IE9。
                
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
                

#### 2) 圣杯布局
> - 多一个div作为container
> - container的左右padding为左右栏留出空位
> - 左右栏使用relative作平移补偿
    

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

#### 3) 简单float布局
> - 左右分别来一个float，中间用margin撑开
> - center只能放在下面，否则会挤掉left和right
> - 缺点：center最后才渲染，而且center的文字流会收到left和right的影响
                
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
#### 4) 绝对float布局
> 多一个div作为包裹
> 简单易用，兼容性好
> 中间最先出
                
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
#### 5) 绝对布局
> 多一个div作为包裹
> 简单易用，兼容性好
> 中间最先出
                
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

<h3 id='6.7'>6.7 弹性布局</h3>

      
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
>>>>>> ![图6-2 flex圣杯布局](https://github.com/hblvsjtu/FET/blob/master/picture/%E5%9B%BE6-2%20flex%E5%9C%A3%E6%9D%AF%E5%B8%83%E5%B1%80.png?raw=true)

<h3 id='6.8'>6.8 响应式布局</h3>

        
#### 1) null
> -
        

<h3 id='6.9'>6.9 变形动画</h3>

        
#### 1) 二维动画
> - 引自[落霞与孤鹜齐飞](https://segmentfault.com/a/1190000015236871)
                
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
#### 2) 三维动画
> - 引自[落霞与孤鹜齐飞](https://segmentfault.com/a/1190000015236871)
> - preserve-3d：保证所有子元素都处于同一个三维空间
> - perspective定义摄像机（也就是作为观众的我们）到屏幕的距离
> - perspective-origin定义摄像机观察到的画面中的灭点（vanishing point）的位置
                
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


<h3 id='6.10'>6.10 补间动画</h3>

        
#### 1) null
> - 
