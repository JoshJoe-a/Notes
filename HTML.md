### HTML

#### 一、www的历史

1. WWW = URL + HTTP + HTML (World Wide Web)

2. WWW/HTML的发明者：Tim Berners-Lee(1990年)

   * 自己写了第一个浏览器
   * 自己写了第一个服务器
   * 用浏览器访问了服务器
   * 发明了WWW、HTML、HTTP、URL

3. 互联网热潮：亚马逊、谷歌、雅虎

4. 万维网在美国的火爆

   * 1993年万维网、Mosaic浏览器出现在人们的视野
   * 1996网站成为上市公司的必需品
   * 网站之后，内容搜索需求激增，谷歌崛起
   * App创业浪潮出现

5. HTML标准制定

   W3C，由Tim Berners-Lee创立

#### 二、HTML基本概念

##### 1. HTML5

* 最新版本的HTML语言，含旧标签和新标签
* HTML5和他的朋友(包括CSS3等)

##### 2.HTML5技术集合

* 新标签、新属性
* 新的通信技术：WebSockets、WebRTC等
* 离线存储技术：Local Storage、断网检测
* 多媒体技术：视频、音频
* 图像技术：Canvas、SVG、WebGL
* Web增强技术：History API、全屏
* 设备相关技术：摄像头、触摸屏
* 新的样式技术：CSS3新的Flex,Grid布局方式

##### 3.H5

* 手机页面

##### 4.HTML语法

* 标签

  ```html
  <!DOCTYPE html>  //文档类型
  
  <tag attr=value>内容</tag>
  <div id="x xx"> √
      内容
  </div>
  
  <tag attr>内容</tag>
  <input checkbox checked>
  
  <tag attr=value/>
  <link rel="stylesheet" href="style.css"> 规范
  ```

* 细节

  * 没有大小写区别
  * 引号：若无特殊要求，可加可不加
  * 注释：`<!--- 注释 --->`
  * 组合

##### 5.HTML标签

###### 英文

|   英文    |  翻译  |    英文     |  翻译  |
| :-------: | :----: | :---------: | :----: |
|  heading  |  标题  |    order    |  顺序  |
|   body    |  正文  |   ordered   | 有序的 |
| paragraph |  段落  |  unordered  | 无序的 |
|  section  |  章节  | description |  描述  |
|  article  |  文章  |    term     |  术语  |
|   main    |  主要  |    data     |  数据  |
|   aside   | 旁边的 |    quote    |  引言  |
|  anchor   |   锚   |    block    |   块   |
|  strong   |  强壮  |   inline    |  行内  |
| emphasis  |  强调  |    break    |  中断  |
| reference |  引用  |    frame    |  框架  |
|   hyper   |  超级  |   canvas    |  画布  |

###### 全局属性

```html
<title>标题</title>
<div id="不唯一" class="常用" style="块内样式">
   优先级:
    xxx.style.border='10px solid black'	> 
    style="border:10px solid green" 	> 
    .bordered{
    	border:10px solid yellow;
    }
</div>
<div contenteditable(可编辑) hidden tabindex(table选中)>
    
</div>
```

###### 默认样式(例如：h1)

* 打开Chrome开发工具

* Elements  Style user agent stylesheet 

###### 常用的内容标签

```html
<!---有序列表--->
<ol>
    <li></li>
</ol>

<!---无序列表--->
<ul>
    <li></li>
</ul>

<!---描述列表--->
<dl>
    <dt>Amyloid</dt>
    <dd>Beauty</dd>
</dl>

<pre>保留所有空格\回车</pre>
<hr>分隔线</hr>
<br>换行</br>
<em>强调:斜体</em>
<code>代码</code>
<quote>引用</quote>
<blockquote>换行引用</blockquote>
```

###### 重点标签

* a标签
  * `<a href="" target="_blank" download rel=noopener></a>`
  * 作用
    - 跳转外部页面
    - 跳转内部锚点
    - 跳转到邮箱或电话等

  * href的取值
    * 网址
      * https://google.com
      * http://gogle.com
      * //gogle.com(无协议的网址)

    * 路径
      * /a/b/c以及a/b/c
      * index.html以及./index.html

    * 伪协议
      * id="xxx"  href='#xxx'
      * JavaScript:代码;
      * mailto:邮箱
      * tel：手机号

  * target取值
    * _blank
    * _top
    * _parent
    * _self


* table标签

  ```html
  <table>
      <thead>
          <tr>
              <th>表头</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td>table date</td>
          </tr>
          <tr>table row</tr>
      </tbody>
      <tfoot></tfoot>
  </table>
  ```

* img标签

  ```html
  <img src="" alt="dog" height="400" style="max-width: 100%;">
  <!---
  src图片的路径
  alt图片加载失败时显示的内容
  height,width设置一个图片自适应，若同时设置可能会导致照片变形
  style="max-width: 100%;"图片自适应
  --->
  ```

* form标签

  * 作用
    * 发出get或post请求
  * 属性
    * action
    * autocomplete
    * method
    * target
  * 事件
    * onsubmit
      * button里面可以有其他标签，onsubmit里不能装其他内容
      * 注意button的类型

* input标签

  * type
    * text
    * color
    * password
    * radio：name="gender"（单选）
    * checkbox
    * file：multiple
    * hidden自动关联ID数