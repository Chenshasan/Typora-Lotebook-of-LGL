# javascript笔记

#### Js是什么

交互、功能

Js就是在修改一些样式

 

#### Js的鼠标提示框：

Js事件：nomouseover=”div1.style.display=block”

原理：修改div的display

事件：onmousrover onmouseout

元素属性操作：1.obj.style.（……） 

​              2.obj.style[……]括号中间的部分可以直接用参数表示 

 

通过<script>和fuction来简化代码

 

重用——合并

变量

Var odiv=document.getElementById(‘div1’)

 

#### 函数基本格式：

Fuction to green（）{

}

 

#### 网页换肤逻辑：

转换css的设定，即转换link中的href

任何标签都可以加id；任何标签的任何属性都可以修改

 

Js里有If选择语句

Eg:if语句例子

如果div是显示的，就隐藏掉

如果div是隐藏的，就显示div

 

链接加上js

<a href=”javascript:;”>链接</a>

 

className的使用:在修改js中的class属性的时候，要用className属性来修改

 

函数传参：类似于c语言中直接传参

 

\1.     style中设置样式 在行间设置

\2.     style中读取样式 在行间读取（不是在样式表中读取）

\3.     className不会修改行间样式，优先级不如style高

 

#### 提取事件

修改onclick属性，且onclick值应该为函数

Function 名字(){

…}

Obtn.onclick=名字

或者使用匿名函数

Obtn.onclick=fuction (){

…..}

 

Window.onload 页面加载完成的时候发生

Window.onload=fuction(){

….}

 

#### 行为、样式、结构三者分离

（别加行间样式和行间行为事件）

 

获取一组元素：getElementsByTagName

可以获取所有的div，以数组形式获取

获取后可通过循环处理（while\for）

 

全选：控制checkbox的checked属性

反选：通过if选择来改变checked的真和假

 

This当前发生事件的元素

可以直接给每个button和div在脚本里加index

innerHTML

html标签中显示的字，如果在脚本中为html的代码，则显示执行该代码之后的结果

 

js数量特别多时用数组处理

 

字符串连接：从左到右依次进行，且字符串和数字相加为字符串，可通过小括号使数字加数字

 

#### Js组成

ECMAscript：js解释器

DOM:document object model   document

操作html的入口

Bom：browser object model 浏览器 window

三个组成的部分为兼容性问题的来源

ECMA  几乎没有兼容性问题

DOM   有一些操作不兼容

BOM   几乎不兼容

 

 

#### 变量类型

检测变量类型：type of 

Number/string/Boolean/function/object/undefined(没有定义或者 定义了没有给类型)/

一个变量应该只存放一种类型的数据

 

#### 字符串转换：

字符串转换成整数：parseInt()  parseFloat()

NaN not a number 非数字

NaN和NaN不相等（对不同元素的NAN判断结果不同）

 

隐式类型转换：==  ===（不转换类型，直接比较）  减法

 

#### 变量作用域

全局变量和局部变量

函数里声明的变量为局部变量

对未声明的变量赋值会直接转换为全局变量

 

#### 闭包

子函数可以使用父函数的局部变量

 

#### 命名规范

类型前缀+首字母大写

 

 

真：true，非零数字，非空字符串，非空对象

假：false，零，空字符串，空对象，undefined

 

#### Json

Var json={a:12,b:5,c:’abc’}

调用：json.a或者json[‘a’]

Json和数组：1.json的下标为字符串，数组的下标为数字

2.Json没有length

3.数组和json都有for(var I in arr){}

 

#### 函数返回值

在哪调用，返回到哪

一次只能返回同一个累型的一个值

 

Arguments 可变参 不定参（参数个数可变） 形式是由所有的不定参组成的数组

 

#### CSS函数

Css(oDiv,’width’)  获取样式

Css(oDiv,’width’,’200px’)  设置样式

 

 

#### 取非行间的样式

oDiv.currentStyle.width(提取css设置的非行间样式)（不兼容）

getComputedStyle((oDiv),null).width)

通过if else解决兼容问题

 

复合样式：background，border

单一样式：width,height,color(getStyle只能提取单一样式)

 

数组的Length既可以获取，又可以设置

#### 数组方法：（相当于arrayList）

Push();pop();(尾部添加删除)

Shift();unshift（头部删除，添加）

Splice()(用来删除元素，传入起点和长度)

（用来插入元素，先删除，再插入，传入起点和长度以及插入的东西）

Join（），替换连接符

Concat链接两个数组

Sort（）调用后直接排序，从A到Z排序，数字排序为第一个数字从小到大排序(当字符串排列)

Arr.sort(function(n1,n2){

If(n1<n2){

Return -1;}

Else if (n1>n2){

Return 1}

Else 

Return 0;

)

 

Arr.sort(function(n1,n2){

Return n1-n2}

可以实现从小到大的数字排列

#### 定时器的使用

定时器：setInterval(show(函数),1000) 每隔一千毫秒执行一次show函数

Timer=SetTimeout(show,1000) 只执行一次

关闭定时器：clearInterval(timer) 同理有clearTimeout

#### 日期对象

Var oDate=new Date();

o.Date.getDate/getHours/getMinutes/getSecond

把数字补成两位数需要自己写程序

 

src的本质是字符串，可以修改字符串中的内容

 

setInterval会有一秒钟的延迟，可以直接在函数中执行该函数消除时间差

 

offSetLeft 获取物体的left属性

offSetTop 获取物体的top属性

 

#### 数码时钟

获取系统时间：Date对象，getHours，getMinutes，getScenonds

显示系统时间：字符串连接，空位补零

设置图片路径：charAt方法

 

#### 延时提示框

移入显示，移出隐藏

移入显示，移出延时隐藏（setTimeout和clearTimeout）

 

#### 无缝滚动

让div移动起来/offsetLeft的作用/用定时器让物体连续移动起来

改变滚动方向：修改speed/修改判断条件

鼠标移入暂停：移入关闭定时器/移出重新开启定时器

 

### DOM基础

什么是DOM？

节点=标签=元素

nodeType 标签的类型：

children/childNodes 计算子节点，且只计算第一层的子节点

nextSebling 兄弟节点

parentNodes 查找父节点

appendChild 添加子节点

offSetParent 查找元素用来定位的父节点（如果父节点定位就用父节点，如果没有就用body）

firstElementChild lastElementChild(高版本) 第一个/最后一个子节点

firstChild lastChild(低版本)

 

setAttribute（名称，值）

getAttribute（名称）

 

#### 创建DOM元素（节点）createElement()

插入元素 insertBefore(节点，原有节点)

删除元素

 

#### 文档碎片

CreateDocumentFragment 

文档碎片：提高低级浏览器性能

 

#### 表格应用

获取：tBodies,tHead,tFoot,rows,cells

#### 隔行变色：鼠标移入高亮

添加（先添加每个td到tr中，然后将tr添加到tbody中），删除（从表格中删除不是直接删除表格的children，而是删除表格的tBodies 的children）一行document的使用

 

#### 搜索

字符串比较

忽略大小写——大小写转换

模糊搜索：Str 有search功能（找到并返回字符串出现的位置）

多关键词:splitcon

 

排序：移动Li

元素排序：转换——排序——插入

 

const定义的变量不可以修改，而且必须初始化。

var定义的变量可以修改，如果不初始化会输出undefined，不会报错。

let是块级作用域，函数内部使用let定义后，对函数外部无影响。

 

#### Console——js调试工具

https://www.cnblogs.com/zhubei/p/6699500.html console用法详解

 

#### js中obj.assign(target,source)方法

![img](file:///C:/Users/李甘霖/AppData/Local/Temp/msohtmlclip1/01/clip_image002.jpg)

替换空对象可以避免原对象本身被修改

 

 