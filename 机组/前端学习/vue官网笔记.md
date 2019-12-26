vue官网笔记

#### V-…  vue特有的相应式指令

- v-bind:title=’message’  title属性与message相对应

- v-if可以改变属性为真或者假 v-if=’seen’

- v-for 绑定数组的数据来渲染一个项目列表 v-for=’todo in todos’

- v-on 添加事件监听器 v-on:click=”reverseMessage” reverseMessage为js文件中的方法

- v-model 表单输入和应用状态的双向绑定 v-model=”message”

 

#### Vue从创建一个vue对象开始

当vue对象被创建时，将data对象中的所有的属性加入vue的响应式系统中

Object.freeze(data) 阻止修改data现有的属性

Vue的实例属性前面有$

 

生命周期钩子：

这里有生命周期钩子的created函数，也有其他的钩子在实例生命周期的不同阶段被调用，如mounted,updated,destroyes。

生命周期的this上下文指向调用它的vue实例

#### 箭头函数没有this

this往往会作为变量向上级词法作用域查找，导致error

- Vue.js使用的是基于HTML的模板语法，所有vue.js的模板都是合法的html，能被浏览器和HTML的解析器解析

- Vue能只能计算出最少需要重新渲染多少组件，并把dom的操作次数减少到最少

#### 插值

双大括号的文本插值能实现数据绑定{{message}}（数据会一直更新）

<span v-once>{{massage}}</span>能实现message插值处的内容只实现一次，不会更新

 

Rawhtml的内容会在v-html指令里面被解析成html语言直接应用在文件中

 

v-bind指令在绑定属性时，如果值为true or false则表明该属性存在或不存在

插值绑定中所有的vue实例会作为javascript被解析，但每个绑定都只能包含单个解析式，同时这个解析式被放在沙盒中，只能访问全局变量的白名单，如math date，但不能访问其他全局变量

 

 

 

有的指令能接受参数，如v-bind v-on

·可以用接受用方括号括起来的javascript表达式作为指令的参数

·<a v-bind:[attributeName]=”url”></a> 方括号中表达式应为字符串，否则值为Null

·表达式为没有空格或者引号的表达式

·浏览器强制把表达式中所有字母转换为小写

 

“.”修饰符

指出指令应该以特殊方式绑定

 

#### 计算属性：

computed{

reversedMessage:function(){

​        return this.message.splite(‘’),reverse(),join(‘’)

}}

·不要直接使用计算式，在表达式中使用计算属性

·计算属性有默认的getter，可以自己设定setter

 

 

v-bind可以绑定对象

如v-bind:class可以被传给对象，动态地切换class

Class会加入active 或者texte-danger

v-bind也可以直接传入数组，或者有for选择语句的数组

v-bind:style的绑定方式有

style=”{color:activeColor,fontSize:fontSize}”（对activeColor和fontSize进行定义）

style=styleObject (对样式对象进行定义)

 

v-if条件语句为表达式的指令返回truthy的时候被渲染

·v-else语句和v-else if的指令紧跟v-if语句

·<tmeplate>上可以使用v-if条件渲染分组

 

Key属性，表达元素是完全独立的，不用复用的

 

v-show元素也可以用于条件展示，但是是修改display，不支持<template>和<v-else>

 

v-for可以将数组应用于绑定v-for：=“item in items”

v-for=”(item,index) in items”所有item共享该元素的其他属性和信息

v-for=”(item,name) in items”可以提供第二个参数的property名称（键名）

 

div v-for=”item in items” v-bind:key=”item.id”
为每一项提供唯一key属性方便vue跟踪每个节点




- 触发试图更新：Push() pop() shift() unshift() splice() sort() reverse() 

- 由于js的限制，vue不能因为利用索引直接设置数组项或者数组长度的变化而引起视图更新（可以用splice() 和set()实现试图更新）

- Vue不能检测对象属性的添加或者删除（但可以用set添加属性）Vue.set(vm.userProfile,’age’,27) 

- 显示过滤/排序后的结果，可以创建计算属性/当计算属性不适用时（如在嵌套for循环中）可以使用方法（原数组）的返回值来实现

- v-for也接受整数，如v-for=”n in 10”

- <template>标签中可以使用v-for来循环渲染包含多个元素的内容

- v-for和v-if可以一起使用，v-for比v-if优先级高（先循环再判断是否有该属性）（可以将v-if置于v-for外层元素上）

- v-on:click=事件表达式

- v-on可以用于监听事件

- v-on可以直接用于绑定Js中的方法

- $event可以直接传入方法，直接访问dom原生事件对象

- v-on的事件修饰符，用点开头的指令后缀表示：.stop/.prevent/.capture/.self/.once/.passive

- v-on:keyup.enter按键修饰符，只有在key是enter状态的时候调用方法

- 按键修饰符：.enter/.tab/.delete/.esc/.space/.up/.down/.left/.right

- 系统修饰键：/.ctrl/.alt/.shift/.meta（只有按键被按住时才能调用事件）

- 鼠标按钮修饰符.left/.right/.middle

- .exact控制由精确的系统组合触发的事件

 

#### 表单输入绑定

v-model指令在表单<input><textarea><select>创建双向数据绑定 

监听用户的输入事件以更新数据

v-model使用的不同的输入元素有不同的属性

- text textarea value属性

- checkedbox和redio checked属性

- select value作为Prop

文本区域插值（<textarea>{{text}}</textarea>）不会生效