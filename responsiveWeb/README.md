## 响应式网站设计 ##

### 一、概念 ###

&emsp;针对一个理想的视觉体验，同时嵌入各种基于互联网标准的技术使其更有弹性，更能适应不同的媒介的呈现。

&emsp;响应式网站是一个设计理念，是多种技术的综合体。

&emsp;响应式设计并不仅限于改变布局。通过媒体查询我们能够相当精确地对页面进行重构：包括在小屏幕上扩大链接的目标区，从而更好的遵循触摸屏的[费茨定律](http://webdesign.tutsplus.com/articles/applying-fitts-law-to-mobile-interface-design--webdesign-6919 "费茨定律")；包括对某些元素有选择性地显示或隐藏，从而改善页面的导航功能；还包括设置[响应式排字法](https://ia.net/know-how/responsive-typography-the-basics "响应式排字法")，渐进地改变字体大小和行距，从而为显示设备提供最优化的阅读体验。

&emsp;三大技术成分：

&emsp;&emsp;1. 弹性网格布局

&emsp;&emsp;2. 弹性图片

&emsp;&emsp;3. 媒介查询

### 二、优点与缺点 ###

1. 优点
&emsp;1. 减少工作量
&emsp;&emsp;1. 网站、设计、代码、内容都只需要一份；
&emsp;&emsp;2. 多出来的工作量只是JS脚本、CSS样式做一些改动；
&emsp;2. 减少时间
&emsp;3. 每个设备都能得到正确的设计
&emsp;4. 搜索优化

<!--more-->

2. 缺点
&emsp;1. 会加载更多的样式和脚本资源
&emsp;2. 设计比较难精确定位和控制
&emsp;3. 老版本浏览器兼容不好

### 三、媒体查询 ###

1. 媒体查询的语句中，**only**尽量不要省略

2. 移动设备：
&emsp;1.布局视口：用来在一个虚拟的窗口下布局页面的
&emsp;2.可视视口：网页在移动设备上呈现出来的大小，即屏幕的大小
&emsp;3.理想视口：布局视口在一个设备上的最佳尺寸。理想视口下的页面便于浏览器、浏览、阅读

**缩放可以改变网页在可视视口的大小，但是不能改变网页在布局视口的大小**

### 四、设计实践原则 ###

1. 渐进增强
2. 优雅降级（正常人类）
3. 先对最新版chrome进行调试
4. 视情况展示网站的内容
5. 断点的选择，即媒体查询的临界点

### 五、如何组织目录结构 ###

1. 约定优于配置
2. 约定代码结构或命名规范来减少配置数量
3. 没有最好的组织方式，只有最合适的

### 六、有用的文件 ###

1. robots.txt：约定搜索引擎蜘蛛爬虫不需要爬的页面
2. humans.txt：关于开发者的简单介绍
3. favicon.ico：网站的图标
4. .editorconfig：编辑器样式约定
5. .gitignore：版本管理时需要排除的一些“垃圾”文件
6. README.md：项目简介、使用方式、相关链接
7. CHANGELOG.md：项目每个版本的更新，说明版本号、更新内容、修复了哪些问题等

### 七、响应式图片 ###

加载与用户设备相匹配的小图片，既快速，又不会影响用户的体验
1. js或服务端
2. srcset:通过高版本浏览器中img标签下的srcset属性来控制什么样的屏幕大小下加载什么样的图片。
&emsp;1. 方法为`srcset="picture1.png 480w, picture2.png 800w"`
&emsp;2. 这个方法中，如果界面从小变到大，则加载的一直是大图片，因为当加载到大图片时，由于浏览器的缓存作用，页面在呈现时会自动调用本地缓存，因此一直会是大图
&emsp;3. 在DDR为2的情况下，并不是严格按照比值来选择何时加载的，会同时考虑网络状况以及图片比例的其他因素
3. srcset配合sizes，sizes的默认值为100vw即百分之百视口宽度。这里还可以添加媒体查询等条件
4. picture：
```html
<pircture>
    <source media="(max-width:36em)" srcset="pic1.png"/>
    <source srcset="pic2.png"/>
    <img class="image" src="pic2.png">
</picture>
```
为img依据不同的媒体查询条件设置不同的srcset属性,还可以通过source的type属性来选择image/svg + xml或者 image/webp。这个webp格式的图片，只有谷歌和安卓支持
5. svg（这种方法还没有尝试过，这里不做讲解，有兴趣的可以自行查阅资料 :innocent:）

---
>&emsp;&emsp;以上是我对响应式开发中总结的一些注意事项，可能并不是很全面，还希望感兴趣的同学可以一起交流学习。:smiley: :smiley: :smiley:
