# head first java笔记

### 1.breadking the surface

java工作方式，输入源代码，通过编译器将源代码编译成字节码，再用JVM使用字节码展示出最后的结果

### 2.A trip to objectville

设计类时，考虑：things the object konws和things the object does

![1569745918022](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1569745918022.png)

类不是对象，类指导对象的生成——class is a blueprint of object

对象和对象之间talks，main函数的主要作用仅仅是启动java程序以及检测实例类

### 3.Know your variables

primitive variable和reference variable，在类中均为instance variable

变量保留码

![1569747911094](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1569747911094.png)

array也是对象，且array托举一系列的variable

### 4.how objects behave

method可以传入一些参数，同时返回一些东西

java ——pass by value即pass by copy

若传入的是基本变量，则改变基本变量的参数值的时候并不改变原参数的值，但若传入的是引用变量，引用变量的copy仍然指向同一个对象，则在方法中可以改变该对象的值

封装

- 使用private来修饰类中的instance variable可以起到封装作用；使用有public修饰的getter和setter方法可以获取该类或者修改该类
- instance variable 是在类中声明，local variable则是在方法中声明；instance variable具有默认值，而local variable没有默认值，必须初始化，默认值列表如下

<img src="C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1569754031680.png" alt="1569754031680" style="zoom:50%;" />

### 5.extra strength methods

设计一个类的步骤：

![1569749606420](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1569749606420.png)

伪代码的主要构成：变量的声明；方法的声明；方法的逻辑

### 6.java API

对ArrayList的基本操作：

![1569754473104](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1569754473104.png)

除了java.lang之外，使用其他包的内容时需要对java其他包做引入

使用HTML api文档来调用api，查阅api的内容

### 7.better living in objectville

继承的要求：能够共用一些相同的特性；在逻辑上有从抽象到具体的关系

继承了同一类A的类B，C，D都能够通过is a A的测试

四种access level：public private protected default

override即为子类重写父类的方法，且override的限制条件有1.两种方法的传入参数要相同，且return的形式要兼容2.两种方法的access level要相同

多态：同一个reference能够调用继承同一类的不同的类

<img src="head first java笔记.assets/1570532597673.png" alt="1570532597673" style="zoom:50%;" />

overloading：两个方法具有相同的名字但有不同的传参，限制条件：不能只改变return type，本质上还是两个不同的方法

### 8.interface and abstract classes

声明抽象类，一个抽象类可以含有抽象方法和非抽象方法

![1570534286024](head first java笔记.assets/1570534286024.png)

abstracrt method

- 这个方法必须被override，这个方法没有body，如果声明了抽象方法，那必须声明抽象类，即一个抽象方法只可能在一个抽象类里面出现

- 继承树中第一个concrete 类必须实现之前所有父类的abstract 方法


所有的类都继承object类，object类有四种基本方法：

![1570535522662](head first java笔记.assets/1570535522662.png)

将更generic的类具体化需要使用强制转换

当抽象类被实例化了之后，抽象类中的方法是可以直接通过抽象类的引用调用的

interface

- 是一个继承关系中类似于父类的存在，但因为interface中所有方法均为abstract的，所以所有的ineterface的方法均需要被重写

- 基本上任何类都可以实现相同的interface，且一个类可以实现多个interface

### 9.constructors and garbage collection

栈和堆

![1570538970410](head first java笔记.assets/1570538970410.png)

- 如果一个局部变量被声明为一个对象，那么只有这个引用本身在栈上，其指向的对象在堆上

- 全局变量在堆上，在它所隶属的对象里



构造函数：constructor 在使用new时，jvm会调用构造函数

![1570622285239](head first java笔记.assets/1570622285239.png)

- constructor类似于方法，但没有返回类型，因为在外部调用返回之前构造函数就已经完成了构造
- 构造函数可用于初始化一些值或者输出
- constructor可以被overload
- instance variable能够有默认值，为0或者Null
- 如果一个子类的constructor被使用了，那么它将唤醒所有父类的constructor
- 如果子类使用constructor的时候没有call super()，那编译器会自动call super()，并且call super()是所有constructor最先完成的事，因此只有当父类constructor完成时，子类的constructor才会被完成
- 当子类继承了父类的getter但没有继承父类的私有变量时，子类继承的方法会去通过super调用父类的方法
- 在构造函数中this()\super()都必须是第一声明，因此不能重复在一个构造函数中同时调用this()\super()

垃圾回收机制

- 对象的存在时间是当其没有被引用时，将会被回收
- 方法中的变量不能够互相调用，在某一方法中调用其他方法时，只要方法还在栈中，其局部变量还是存在（只是不能被其他方法调用）

### 10.numbers and statics

static方法

- 即为不依赖类中任何全局变量的方法，因此static方法不需要通过创造对象然后通过对象名调用，而是直接通过类名调用
- 如Math类中的方法直接通过类名调用，且Math类中地constructor被设定为private，即Math类不能被new
- 静态方法也不能调用非静态方法

static变量

- one value for one class instead of one value for one instance
- static变量只在类被加载的时候初始化，而不是在对象被创建的时候都初始化
- 初始化顺序：static变量=>static方法/object
- 访问static变量时也像static方法一样直接通过类名调用
- static变量也有初始值

final修饰符：表明变量被声明以后就不能更改，方法被声明后不能再被voerride，类被声明后不能再被继承

static final表示这个变量不能更改且和整个类保持相同的存在时间，且该变量必须在初始化的时候声明，有如下两种声明方式

![1570948190324](head first java笔记.assets/1570948190324.png)

![1570948202312](head first java笔记.assets/1570948202312.png)

Math类中的方法：

- Math.random()（随机取值）
- Math.abs()（取绝对值）
- Math.min()
- Math.max()
- Math.round()（取整）

基本数据类型的打包：（将基本数据类型当做对象处理）

![1570948899329](head first java笔记.assets/1570948899329.png)

Autobox：将基本数据类型和对象类型能够一起使用，即在使用wrapper对象的时候和基本类型是互相兼容的，如传参，返回参数时

![1570951800631](head first java笔记.assets/1570951800631.png)

以下为autobox所使用的范围

![1570952047346](head first java笔记.assets/1570952047346.png)

![1570952107092](head first java笔记.assets/1570952107092.png)

wrapper对象也拥有static方法，如

![1570952203176](head first java笔记.assets/1570952203176.png)

Sring.format()方法：将数字也通过string的方法输出

![1571144332596](head first java笔记.assets/1571144332596.png)

![1571144405636](head first java笔记.assets/1571144405636.png)

format的主要形式：format中precision是强制必须有的，%d代表十进制，%f代表浮点数，%x代表十六进制，%c代表char

![1571217032361](head first java笔记.assets/1571217032361.png)

当用format表示日期时，为

![1571217524245](head first java笔记.assets/1571217524245.png)

可使用Calender包表示java日期，但Calender类是抽象的，因此使用getInstance方法来实例化Calender的子类

![1571217902245](head first java笔记.assets/1571217902245.png)

![1571218203117](head first java笔记.assets/1571218203117.png)

### 11.exception handling

java sound API:MIDI 对于声音进行处理，然后将该数据通过MIDI播放器播放出来，sequencer是将数据顺序化处理以便于其播放出完整音乐

![1571226092336](head first java笔记.assets/1571226092336.png)

启动播放：

![1571226177832](head first java笔记.assets/1571226177832.png)

MIDIevent信息：（MIDImessage：表明做什么）和什么时候开始做

![1571226458251](head first java笔记.assets/1571226458251.png)

MIDImessage包含信息：

![1571226683277](head first java笔记.assets/1571226683277.png)

异常处理：

- 异常可由方法抛出，抛出该异常前必须声明，异常会被抛出到方法的调用者，调用者可通过try/catch处理。

- 所有的异常都会被编译器检测出来，除了runtime exception

- ![1571223010464](head first java笔记.assets/1571223010464.png)

- finally块的代码在不管是否抛出异常时都执行

- 多异常处理：先处理小的异常再处理大的异常

- ![1571223601060](head first java笔记.assets/1571223601060.png)

- 在抛出异常和接收异常时，都能够通过父类的类型来抛出（捕获）子类的类型

- 如果方法中调用的其他方法抛出异常且该方法不想处理该异常，则该方法也声明抛出异常即可，但main必须处理所有的异常

  ![1571225623630](head first java笔记.assets/1571225623630.png)

- 其余规则：![1571225928801](head first java笔记.assets/1571225928801.png)

### 12.getting gui

基本的gui界面：

![1571302099148](head first java笔记.assets/1571302099148.png)

在画基本界面时Jframe必须要getContentPane以及setSize和setVisible，才能将Jframe表示出来

widget包括 ：JButton,JRadioButton,JCheckBox,JLable,JList,JScrollPane,JSider,JTextField,JTextArea,JTable

- 监听Jbutton按钮事件是否被触发——listener interface，回调函数就在这个interface中
- 在Java中一个事件被认为是一个对象，每种事件类型都对应一个listener interface
- 每个事件类型中都有可能有多种方法，如移到鼠标上，点击鼠标等
- button通过addActionListener添加接口，actionperformed方法能够被传入源事件（如鼠标点击等），然后触发新的事件

![1571303047048](head first java笔记.assets/1571303047048.png)

调用listener：

![1571303158816](head first java笔记.assets/1571303158816.png)

在Jpanel上画图形：

![1571304775494](head first java笔记.assets/1571304775494.png)

![1571304808041](head first java笔记.assets/1571304808041.png)

关于Graphics: 

- grapfics2D的方法包括： fill3DRect(), draw3DRect(), rotate(), scale(), shear(), transform( )
- graghics2D的方法使用时必须将graghics类强制转换成graphic2D类型，这样才能使用graphics2D类型的方法
- 在Jpanel上面画图形时，使用类继承jpanel类，然后再override Jpanel的paintComponent方法，并且这个方法有一个自动传入的参数grphics

实现多个button的监听：

- 通过内部类来实现，内部类能够访问frame等参数的方法同时能够调用不同的Interface，则实现多个监听即创建不同的listener类来实现ActionListener（actionperformed方法是在listener类中的）
- 内部类在其外部类中实现时必须实例化，而且实例化的空间用的是外部类的变量空间

![1571396512688](head first java笔记.assets/1571396512688.png)

实现message events：在sequence上添加ActionListener，可以用来监听，如controllerChange就是对于该接口方法的重写

![1571398867356](head first java笔记.assets/1571398867356.png)

如果该声音信息需要修改面板，可直接添加内部类监听controllerChange，如果有MIDIevent则修改面板信息

### 13.using swing

![1571401860790](head first java笔记.assets/1571401860790.png)

layout manager——在询问组件的要求之后，自行对于页面的布局进行排布和调整

三种layout布局形式：

- border layout，分为5个布局块，每个布局块都只能放置一个组件（北边和南边的版块获得他们想要的高度，而东边和西边的版块获得想要的宽度，中间的版块获得剩下的部分）

- flow layout，水平布局块，layout的默认布局方式，先水平排布，当水平排布已经到达一行的最大限度时再往下排布

  ![1571403285895](head first java笔记.assets/1571403285895.png)

- box layout，垂直排布，每一行只能有一个组件

在panel中设置boxLayout:

![1571403650503](head first java笔记.assets/1571403650503.png)

对于jTextField：

![1571973573467](head first java笔记.assets/1571973573467.png)

使用JTextArea:

![1571974763661](head first java笔记.assets/1571974763661.png)

JCheckBox:

![1571974935387](head first java笔记.assets/1571974935387.png)

JList:

![1571974999062](head first java笔记.assets/1571974999062.png)

GUI的确立顺序基本为：frame,layout,jpanel(add layout)，其他组件（如jTextArea需要先在scrollbar中被确定，botton，box等）

栅栏组件的添加：

![1571976026524](head first java笔记.assets/1571976026524.png)

### 14.serialization and file I/O

- 当文件仅被其他java文件使用时，serialization，即用一个文件保存该序列化文件再被其他java文件启用即可
- 当文件被其他语言文件应用，写成plain text 文件

![1571981914941](head first java笔记.assets/1571981914941.png)

文件的序列化输出为：先用一个fileOutPutStream来连接其他文件，再用ObjectOutPutStream来写入object并连接FileOutPutStream，写完后关闭ObectOutPutStream

![1571982179400](head first java笔记.assets/1571982179400.png)

![1571982413918](head first java笔记.assets/1571982413918.png)

1. 序列化自动的过程是：序列化一个类，并且这个类中引用的所有类，以及引用类中的所有类都会被序列化

2. 实现序列化时，需要声明该类是implements serializable，且接口的实现时可以继承的，即父类实现了该接口，子类无需声明也自动实现该接口

3. 如果可序列化的类中调用了其他的不可序列化的类，会报错

4. 将变量声明为transient即可在序列化的过程中跳过该变量

   ![1571983579663](head first java笔记.assets/1571983579663.png)

还原序列化：需要读取object并且将该object强制转化

![1571983818472](head first java笔记.assets/1571983818472.png)

对于file类可以有如下操作：file类更类似于一个文件的地址，而不是文件本身

![1571986480229](head first java笔记.assets/1571986480229.png)

Buffer：类似于cache，可以先将数据缓存在buffer中，再将buffer连接到file上

![1571986879575](head first java笔记.assets/1571986879575.png)对于文件的读写有fileWrite和fileReader，相应的也有BufferWrier和BufferReader

![1571987104700](head first java笔记.assets/1571987104700.png)

解序列化出错：序列化一个对象之后，修改了该对象的类，再用修改后的类解序列化该对象会出错，以下方式会导致解序列化的出错：

![1571987855481](head first java笔记.assets/1571987855481.png)

版本控制序列号：serial vision UID

当对于一个对象进行了序列化之后，如果后来的类修改了，原则上需要修改版本序列号，表明该类与原对象不兼容，此时JVM不会编译，但是当该类不修改版本序列号时，JVM会编译，此时需要注意修改后的类仍然需要能够处理该对象的解序列化

![1571988178952](head first java笔记.assets/1571988178952.png)

### 15.networking and threads

服务器与客户端的基本工作原理：服务器接收所有客户端的消息并同步给所有客户端



![image-20191104120717499](head first java笔记.assets/image-20191104120717499.png)

#### 客户端

客户端如何具体地连接到服务器并输入与输出信息：

![image-20191104121155766](head first java笔记.assets/image-20191104121155766.png)

socket能够建立服务端和客户端之间的联系，让两边都能够连接到对方：

- Socket中的数据是服务器的数据，能够让客户端连接到服务器，服务器通过等待请求以后再建立一个Socket即可

- TCP port能够使用从0到65535中间的任何数组，但是0到1023是用于被公认的服务请求，所以一般使用104到65535中间的数字

- IP地址确定一个具体的位置，而TCP port则确定具体位置的具体方式/地点

![image-20191104121455583](head first java笔记.assets/image-20191104121455583.png)

通过BufferReader从socket上面读取信息：

1. 建立socket联系
2. 从socket上读取inputStream
3. 通过BufferReader储存输入流的信息，同时读取BufferReader的信息

![image-20191104131624705](head first java笔记.assets/image-20191104131624705.png)

通过WriterPrint输送信息到Socket上

1. 建立Socket联系
2. 建立PrintWriter
3. 写PrintWriter

![image-20191104132007709](head first java笔记.assets/image-20191104132007709.png)

#### 服务器

1. 建立服务器的ServerSocket
2. 通过clinet的Socket建立一个新的Socket和客户端交流

![image-20191104132605402](head first java笔记.assets/image-20191104132605402.png)

#### 线程

java通过线程实现多步同时进行，通过java类Thread的实例化构建新进程即可

新的进程也占用栈中的内存，且在调用新进程时，主进程是被停止的：

![image-20191104143413978](head first java笔记.assets/image-20191104143413978.png)

开始一个进程的步骤：

1. 通过Runnable类创建对象，明确进程的任务
2. 创建进程
3. 开启进程

![image-20191104143547360](head first java笔记.assets/image-20191104143547360.png)

通过自己定义类继承Runnable接口，在该类中的run和go方法中明确要做的任务，然后通过线程类来启动runnable类

![image-20191104144052109](head first java笔记.assets/image-20191104144052109.png)

- 线程控制器能够选择运行什么线程，线程控制器在不同的JVM上面可能不一样，因此相同的程序在不同的JVM上跑可能会有不一样的结果

- thread.sleep（毫秒数）能够使线程停止该毫秒数的时间，当其醒过来后会再次进入到runnable state，等到线程控制器再次调用这个线程
- 可以通过sleep来调控线程进行的先后顺序

#### 线程锁

当几个线程都调用同一个数据时，在一个线程对一个数据调用的过程中，应该对其有线程锁，防止其他线程调用

- 有线程锁的方法用synchronized修饰
- 线程锁是每个类所具有的的，不是每个synchronized方法锁具有的，也就是当一个线程访问了该类的synchronized方法，这个类的线程锁被锁起来，在synchronized方法访问完之前，其他的任何线程都不能访问该类的任何一个synchronized方法
- 线程死锁：两个进程同时都没有进行完，但都同时拥有对方能进行完的钥匙，所以会产生死循环式的等待