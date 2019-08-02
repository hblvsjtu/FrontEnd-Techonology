# FET

## 作者：冰红茶  
    
------    
    
平常在生活中或者工作中不断的学习前端知识，记录和分享吾之所见吾之所悟^_ ^

## 目录
## [九、浏览器篇](#8)
### [9.1 访问一个链接发生的全过程](#9.1)
### [9.2 浏览器渲染过程](#9.2)
### [9.3 defer和ansys的区别](#9.3)
### [9.4 IE的hack写法](#9.4)
### [9.5 浏览器性能和计时器](#9.5)
### [9.6 HTTP状态码](#9.6)
### [9.7 常见的网络安全问题](#9.7)

        
------      
        
<h2 id='9'>九、浏览器篇</h2>
<h3 id='9.3'>9.3 defer和async的区别</h3>

        
#### 1) 相同点
> - 都用在script的异步脚本加载中，
#### 2) 不同点
> - 脚本的执行时间和执行顺序
> - async的脚本是看那个脚本最先下载完成先执行，跟写在HTML上的顺序是不同的
> - defer实在DOM解析完成后，DOMContentLoaded 事件触发之前完成的，一般是按照写在HTML上的顺序执行，但是实际体验下来这个顺序不能保证
>>>>>> ![图9-1 async和defer的区别](https://github.com/hblvsjtu/FET/blob/master/picture/%E5%9B%BE9-1%20async%E5%92%8Cdefer%E7%9A%84%E5%8C%BA%E5%88%AB.png?raw=true)
<h3 id='9.5'>9.5 浏览器性能和计时器</h3>

        
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
                
                .cube { 
                    -webkit-transform: translateZ(0); 
                    -moz-transform: translateZ(0); 
                    -ms-transform: translateZ(0); 
                    -o-transform: translateZ(0); 
                    transform: translateZ(0);
                }
> - 在 Chrome 和 Safari中， 以下声明可以解决转换或动画可能会看到闪烁的效果
                
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
> - 那问题来了，为什么开启3D来打开GPU加速可以优化动画性能呢？因为浏览器DOM渲染需要经过重排和重绘两个过程，其中重排的消耗最大。那问题就来到如果减少重排和重绘，甚至避免重排和重绘，借此提高动画的性能。动画是有帧组成的连续画面，开启GPU加速，即是GPU计算'层'，或者叫「纹理」，实际上是是DOM快照，通过已知变换矩阵来修改'层'，实质上是位图，来避免DOM的重排和重绘。
> - 那问题又来了：什么情况下会触发层的创建呢？引自[chokcoco的回答](https://github.com/ccforward/cc/issues/42)
>> - 3D 或透视变换(perspective、transform) CSS 属性
>> - 使用加速视频解码的 元素
>> - 拥有 3D (WebGL) 上下文或加速的 2D 上下文的 元素
>> - 混合插件(如 Flash)
>> - 对自己的 opacity 做 CSS 动画或使用一个动画变换的元素
>> - 拥有加速 CSS 过滤器的元素， 如：
                
                filter: brightness(50%); // 明度滤镜
                filter: saturate(1000%); // 饱和度滤镜
                filter: blur(5px); // 模糊滤镜
                filter: hue-rotate(45deg); // 色相反转滤镜
                filter: invert(100%); // 颜色反转滤镜
                filter: contrast(25%); // 对比度滤镜
                filter: drop-shadow(5px 5px 5px red); //阴影滤镜 第一个值是X方向上的位移，第二个值是Y轴方向上的位移，第三个值是模糊的大小，第四个值是模糊的颜色。

>> - 元素有一个包含复合层的后代节点，换句话说，就是一个元素拥有一个子元素，该子元素在自己的层里)
>> - 元素有一个 z-index 较低且包含一个复合层的兄弟元素(换句话说就是该元素在复合层上面渲染
