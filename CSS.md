# CSS

### 一、CSS历史

#### 1.CSS的发明者_Hakon Wium Lie

* 1994年首先提出CSS概念而闻名
* 1999年任Opera的CTO
* 2006倡议Web网页应使用通用字体格式
* 2007倡议浏览器可以支持Video标签
* Web打印概念的倡导者

#### 2.CSS说明

* <span style="color: #4185cd;text-decoration: underline;"><b>CSS</b></span>的全称的<span style="color: #4185cd;text-decoration: underline;"><b>Cascading Style Sheets</b></span>,<span><b>中文称为层叠样式表</b></span>。CSS是一种用来表现<span style="color: #4185cd;text-decoration: underline;">HTML</span>(标准通用标记语言的一个应用)或<span style="color: #4185cd;text-decoration: underline;">XML</span>(标准通用标记语言的一个子集)等文件样式的计算机语言‌。

* 类型

  > * 样式层叠
  >
  >   > 可以**多次**对**同一选择器**进行样式声明
  >   >
  >   > ```css
  >   > p{
  >   >     font-size:100px;
  >   > }
  >   > p{
  >   >     color:red;
  >   > }
  >   > ```
  >
  > * 选择器层叠
  >
  >   > 可以用**不同选择器**对**同一元素**进行样式声明
  >   >
  >   > ```css
  >   > /*<p class="p1"></p>*/
  >   > 
  >   > p{
  >   >     font-size:100px;
  >   > }
  >   > p{
  >   >     color:red;
  >   > }
  >   > .p1{
  >   >     color:green;
  >   > }
  >   > ```
  >
  > * 文件层叠
  >
  >   > 用**多个文件**进行层叠
  >
  > * 说明
  >
  >   > 层叠特性使CSS极度灵活，同时也留下了隐患
  >   >
  >   > CSS2.1使用最广泛的版本
  >   >
  >   > 浏览器支持哪些特性，使用caniuse.com

### 二、CSS学习

#### 1.学习语言

+ 语法（如何写代码）
+ 如何进行调试
+ 在哪里查资料
+ 标准制定者是谁

#### 2.学习路径

* Copy-抄文档，抄老师
* Run-将代码放在自己的机器上运行
* Modify-加入一点自己的想法，然后重新运行

#### 3.CSS语法

##### 语法一：样式语法

* 格式

  > 选择器{
  >
  > 属性名：属性值；
  >
  > /***注释***/
  >
  > }
  >
  > ```css
  > p{
  >     color:red;
  >     font-size:100px;
  > }
  > /*注释*/
  > ```

* 注意事项

  * 所有符合都是英文，写错浏览器会警告
  * 区分大小写，a/A是不同的东西
  * 注释格式`/**/`而非`//`
  * 最后一个分号可以省略，但不建议
  * 任何地方写错了都不会报错，浏览器会直接忽略

##### 语法二:@语法

+ 格式

  ```css
  /*声明字符编码*/
  @charset "UTF-8";
  /*导入额外的CSS文件*/
  @import url(2.css);
  /*媒体查询*/
  @media(min-width:100px) and (max-width:200px){
      /*语法一*/
  }
  ```

+ 注意事项

  + `@charset`必须放在第一行
  + 前两句语法必须以分号结尾
  + `@charset`是字符集的意思，但`UTF-8`是字符编码encoding，这是历史遗留问题

#### 4.文档流

##### 1) 文档流-Normal flow

* 流动方向
  * inline元素从左到右，到达最右边才会换行<span>
  * block元素从上到下，每个都另起一行<div>
  * inline-block也是从左到右，**但不会跨两行**
  
* 宽度
  * inline宽度为内部inline元素宽度的和，**不能用width指定**
  * block默认自定计算宽度（不是100%，是auto），可能用width指定
  * inline-block结合两者特点，**可能用width指定**
  
* 高度
  * inline高度由**line-height间接确定**，跟height无关
  
  * block高度由**内部文档流元素决定**，可以设height
  
  * inline-block与block类似，**可以设height**
  
    ```css
    /*<div>
    	<span>span元素</span>
    </div>
    */
    span{
        border:1px solid red;
        padding:20px;
    }
    
    div{
      border:1px solid green;  
    }
    
    body{
        padding:20px;
    }
    ```
  
* 说明
  * 元素无inline和block的类别之分，可设置其`display`属性
  
    ```css
    span{
        display: inline;
        /*or display: block;*/
    }
    ```
  
  * 注意
  
    * 不要在inline元素内部使用block元素
  
    * 不要写width：100%,会造成bug
  
    * 当内容大于容器时，会溢出
  
      ```css
      div{
          width:300px;
          overflow:auto;
          overflow:scroll;
          overflow:hidden;
          overflow:visible;
          
          overflow-x:auto;
          overflow-y:auto;
      }
      ```

#### 5.盒模型

##### 1)类型

![盒模型](images\boxmodel.jpg)

+ 概念
  + content-box - 内容就是盒子的边界
  + border-box - 边框是盒子的边界
+ 公式
  + content-box width - 内容宽度
  + border-box width = 内容宽度 + padding + border

##### 2）Margin合并

* 触发条件
  * 父子元素间的margin合并
  * 兄弟元素间的margin合并
  * 只存在上下合并，不存在于左右合并
* 阻止合并
  * 取消父子间元素的合并
    * `border`、`padding`、`overflow：hidden`、`display:flex`
  * 取消兄弟间元素的合并
    * 可以使用`inline-block`

##### 3）基本单位

> * 长度
>
>   > * 整数
>   > * 百分比
>   > * px像素
>   > * em相当于自身font-size的倍数
>   > * VW和VH
>
> * 颜色
>
>   > * 十六进制：#000000
>   >
>   > * RGBA：rgb(0,0,0,1)
>   >
>   > * hsl：(360,100%,100%,0.5)/(色相，饱和度，亮度，透明度)

#### 6.CSS布局

##### 1）类型

* 固定宽度布局
  * 一般为960/1000/1024px
* 非固定宽度布局
  * 主要依靠文档流原理布局（手机/H5）
* 响应式布局
  * PC固定宽度，手机不固定宽度（混合布局）

##### 2）布局方式

<img src="images\布局设置.png" alt="布局选择" style="zoom:80%;" />

##### 3）Float布局

* 使用

  * 子元素上加`float:left`和`width`

  * **在父元素上加`.clearfix`**

    ```css
    .clearfix::after{
        content:'';
        display:block;
        clear:both;
    }
    ```

* 注意

  * 有经验的开发者会留一些空间或最后一个div不设width
  * 此种布局不需要做响应式**专为IE准备的**，因为手机上不使用IE浏览器
  * IE6/7存在双倍margin bug，解决
    * 针对IE6/7把margin减半`_margin-left:5px`
    * 设置`display:inline-block`

##### 4）Flex布局

* 基本知识及术语

  * 由于 flexbox 是一个整体模块，而不是单个属性，因此它涉及很多内容，包括其整个属性集。其中一些属性应设置在容器（父元素，称为“弹性容器”）上，而其他属性应设置在子元素（称为“弹性项目”）上。
  * 如果“常规”布局基于块和内联流方向，则弹性布局基于“弹性流方向”。请看规范中的这张图，它解释了弹性布局背后的主要思想。

* 弹性框属性

  * **container**

    <img src="images\container.png" alt="container" style="zoom:60%;" />

    ```css
    /*父级（弹性容器）的属性*/
    .container {
      display: flex; /* or inline-flex */
    }
    
    /*弹性方向*/
    .container {
      flex-direction: row | row-reverse | column | column-reverse;
    }
    
    /*弹性包裹*/
    .container {
      flex-wrap: nowrap | wrap | wrap-reverse;
    }
    
    /*弹性流是否折行*/
    .container {
      flex-flow: row wrap | column wrap;
    }
    
    /*主轴对齐方式*/
    .container {
      justify-content: flex-start | flex-end | center | space-between | space-around | 					  space-evenly | start | end | left | right;
    }
    
    /*次轴对齐方式*/
    .container {
      align-items: stretch | flex-start | flex-end | center | baseline;
    }
    
    /*多行内容*/
    .container {
      align-content: flex-start | flex-end | center | space-between | space-around | 				  space-evenly | stretch | start | end | baseline;
    }
    ```

  * **items**

    <img src="images\items.png" alt="items" style="zoom:60%;" />

    ```css
    /* 控制它们在弹性容器中的显示顺序 */
    .item {
      order: 5; /* default is 0 */
    }
    
    /*项目应占用弹性容器内可用空间的量*/
    .item {
      flex-grow: 4; /* default 0 负数无效*/
    }
    
    /*弹性项目在必要时收缩的能力*/
    .item {
      flex-shrink: 3; /* default 1 负数无效*/
    }
    
    /*控制基准宽度*/
    .item {
      flex-basis:  | auto; /* default auto */
    }
    
    /*属性合并*/
    .item {
      flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
    }
    
    /*控制某一item的对齐方式*/
    .item {
      align-self: auto | flex-start | flex-end | center | baseline | stretch;
    }
    ```

* 弹性盒子小游戏

  * 链接: flexboxfroggy.com

##### 5） Grid布局

* 基本知识及术语

  CSS 网格布局（又名“Grid”或“CSS Grid”）是一种基于网格的二维布局系统，与过去的任何网页布局系统相比，它彻底改变了我们设计用户界面的方式。

* 弹性框属性

  * **container**

    ```css
    .container {
      display: grid | inline-grid;
    }
    
    /*设置行高和列宽*/
    .container {
      grid-template-columns: ...  ...;
      /* e.g. 
          1fr 1fr
          minmax(10px, 1fr) 3fr
          repeat(5, 1fr)
          50px auto 100px 1fr
      */
      grid-template-rows: ... ...;
      /* e.g. 
          min-content 1fr min-content
          100px 1fr max-content
      */
    }
    
    /*or*/
    .container {
      grid-template-columns: [first] 40px [line2] 50px [line3] auto [col4-start] 50px [five] 40px [end];
      grid-template-rows: [row1-start] 25% [row1-end] 100px [third-line] auto [last-line];
    }
    
    .container {
      grid-template-columns: repeat(3, 20px [col-start]);
    }
    ```
    
  * **items**
  
    * 代码
  
      ```css
      /*通过网格线来确定网格项在网格中的位置*/
      .item {
        grid-column-start: <number> | <name> | span <number> | span <name> | auto;
        grid-column-end: <number> | <name> | span <number> | span <name> | auto;
        grid-row-start: <number> | <name> | span <number> | span <name> | auto;
        grid-row-end: <number> | <name> | span <number> | span <name> | auto;
      }
      ```
  
    * 示例
  
      <img src="images\grid-column-row.png" alt="grig-column-row" style="zoom: 80%;" />
  

##### 6）CSS定位

* 定位/布局的区别

  * 布局是屏幕平面上的
  * 定位是**垂直于屏幕**的

* div分层

  <img src="F:\Markdown文档\images\css-position.png" alt="CSS定位" style="zoom: 50%;" />

* position属性

  * 属性值
    * static默认值，待在文档流里
    * relative相对定位，升起来，但不脱离文档流，配合`z-index`使用
    * absolute绝对定位，定位基准是祖先中的第一个非static
      * 某些浏览器如果不写`top/left`会位置错乱
      * 善用`left:100%`或`left:50%`+负`margin`
    * fixed固定定位，定位基准是viewport
      * 常用于广告或回到顶部的按钮
      * 手机上尽量不使用这个属性
    * sticky粘滞定位
  * 说明
    * 若使用`position:absolute`，在其父元素补一个`position:relative`
    * 若使用`position:absolute | fixed`，一定要补`top: 2px`和`left:2px`
    * sticky兼容性差，不经常使用

* 层叠上下文

  * 内容

    <img src="images\cengdie.png" alt="层叠上下文" style="zoom: 33%;" />

  * 可以创建层叠上下文的属性

    * `z-index`
    * `flex`
    * `opacity`
    * `transform`

  * 负`z-index`与层叠上下文

    + 负`z-index`逃不出小世界

##### 7）CSS动画

* 动画
  * 由许多静止的画面（帧）以一定的速度连续播放时，肉眼产生的错觉
  * 帧：每个静止的画面都叫做帧，每秒播放的帧数称为播放速度
  * 方式：修改`left`或`transform`
  
* 浏览器渲染原理

  * 根据 HTML 构建 HTML 树（ DOM )

  * 根据 CSS 构建 CSS 树（ CSSOM )

  * 将两棵树合并成一颗渲染树（ render tree )

  *  Layout 布局（文档流、盒模型、计算大小和位置）

  * Paint 绘制（把边框颜色、文字颜色、阴影等画出来）

  * Compose 合成（根据层叠关系展示画面）

    <img src="images\DOM-Tree.PNG" alt="文档树" style="zoom: 50%;" />

* JavaScript更新样式

  * `div.style.background='red'`
  * `div.classList.add('red')`
  * `div.remove()`

* transform

  * 常用功能：位移、缩放、旋转、倾斜
  * 建议搭配transition使用

* transition

  * 作用：添加中间帧
  * 使用：`transition:属性名 时长 过渡方式 延迟`

* animation

  ```css
  #demo{
      animation:xxx 1.5s;
  }
  
  @keyframes xxx{
      0%{
          transform:none;
      }
      60%{
          transform:translateX(200px);
      }
      100%{
          transform:translateX(200px) translateY(200px);
      }
  }
  ```

  
