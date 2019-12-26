Algorithms (forth edition) 笔记

### 排序：

#### 1.选择排序

每一次取出剩余项中最小的一项，排到最前面，直到所有项全都被排好

#### 2.插入排序

每一次取出一项，插入到前面已经排序的项之中

#### 3.Shell 排序

设定一个n，在一串长数组之中每隔n个抽取一个数形成小型数列，将小型数列进行排序，然后逐渐缩小n到一，完成最终的排序（O（n的二分之三次方））

![1570536951190](Algorithms (forth edition) 笔记.assets/1570536951190.png)4.merge排序

结合两个顺序数组来组成更大的顺序数组。

Top-down mergesort，不断将数组分成更小的数组，直到可以进行两两比较，再进行合并，合并到最大数组为止

=>提升top-dowm mergesort的效率，可以通过用insertion sort排布小型数组，检测数组是否已经排好顺序，消除复制到辅助数组的操作

![1570536977208](Algorithms (forth edition) 笔记.assets/1570536977208.png)

bottom-down mergesort近似于top-down mergesort，通过递归进行排序，先两两比较，再四个之间进行比较，再八个之间进行排序类推到最后合成最终数组

（所有基于比较的排序算法最少的次数只能达到NlogN次级别）

#### 5.quicksort

基于divide and conquer进行排序，基本算法为——选取第一个数，然后将大于它的排在一遍，小于他的排在一遍，再将两边的数进行排序

在每一次排序中都使用隔板将两边的数隔开（通过递归实现），最终完成排序（每次的隔板选择都具有随机性，因此这个算法也具有随机性）

![1570536997092](Algorithms (forth edition) 笔记.assets/1570536997092.png)

Entropy-optimal sorting，类似于quicksort，但将与隔板数相同大小的数也归为一类，用三类区分隔板

![1570537019884](Algorithms (forth edition) 笔记.assets/1570537019884.png)

#### 6.priority queues

这是一种所有逻辑近似于冒泡排序的方式，将顺序先进行heap sort然后再sortdowm,主要算法如下

![1570537033798](Algorithms (forth edition) 笔记.assets/1570537033798.png)

前期有较多的预备知识，如priority queues的基本操作是不断的插入并进行最大值的取出，这一操作同时在heapsort里面蕴含了swim() 和 sink()两种方法，

![1570537068266](Algorithms (forth edition) 笔记.assets/1570537068266.png)

swim()是将小的数字移上去

![1570537083757](Algorithms (forth edition) 笔记.assets/1570537083757.png)

sink()是将数字再进行正常排列

![1570537099925](Algorithms (forth edition) 笔记.assets/1570537099925.png)

这两种方式构成了sortdown的基本逻辑，即不断将最小的数字移到第一位（原第一位作为最大数被去除），再将所有的链进行sink()排列好

而heap constuction就是用sink()将序列整理好，方便sortdown的进行。

heapsort使用了最多2NlgN次的交换和比较次数

#### 7.应用

排序方法的选择

![1570537120097](Algorithms (forth edition) 笔记.assets/1570537120097.png)

=>quick sort往往是最快的排序方法，但如果稳定性很重要且空间足够，可以选择mergesort，有些情况下可以选择不用comparator来进行比较，直接比较基本数据即可

（具有稳定性的排序方法有insertion sort and mergesort）

### 搜索：

#### 1.elementary symbol tables

最基础的搜索表单有如下应用：

![1570537134838](Algorithms (forth edition) 笔记.assets/1570537134838.png)

作为搜索表单，基本api为

![1570537165015](Algorithms (forth edition) 笔记.assets/1570537165015.png)

表单的基础查找方式为二分法查找，这种查找方式要求在插入数据时，先将数据排好 ，在搜索数据是，选择数组中间的key（mid），如果给定的key大于key（mid）则在右边的子数组中找，小于key（mid）则在数组左边的子数组中找。

![1570537182999](Algorithms (forth edition) 笔记.assets/1570537182999.png)

查找时最多使用lgN+1次比较，插入数据时最多为2的n次方次进入数组。

#### 2.binary search trees

一个二分树也是基本树状，每个节点有两个支树，左支树上面的节点都比源节点小，右支树上面的节点都比源节点大

![1570537199997](Algorithms (forth edition) 笔记.assets/1570537199997.png)

基本操作有search 和 insert

search操作由get()方法实现，基本逻辑就是沿着二分树的特质进行搜索，如果树中有这个节点则进行匹配并返回答案，没有则返回null

![1570537214244](Algorithms (forth edition) 笔记.assets/1570537214244.png)

insert操作由put()方法实现，搜索逻辑类似于get(),搜索到具体位置后插入节点

![1570537227756](Algorithms (forth edition) 笔记.assets/1570537227756.png)

寻找minimum和maximum就是找到最左边或者最右边的支树

selection操作有一个rank k，selection是选出从小到大第k+1位的数，即这个节点有k个比他小的节点，算法逻辑是不断往左树上找，如果现有的一个节点左树的节点大于k，则进入这个左树寻找，如果现有的节点小于k，则k=k-左树节点数-1（这个1是现在立足的节点），然后进入右树寻找，直到k为0

![1570537243651](Algorithms (forth edition) 笔记.assets/1570537243651.png)

floor 和ceiling操作，floor是寻找恰好小于k的一个数

![1570537257347](Algorithms (forth edition) 笔记.assets/1570537257347.png)

delete操作，是删除节点，如果节点只有一个子节点，则直接用子节点替代它，如果节点有两个以上子节点，则选择恰好大于它的一个子节点替代他

![1570537272486](Algorithms (forth edition) 笔记.assets/1570537272486.png)

#### 3.balanced search tree

（在这里吹爆algorithm，维基上红黑树的讲解我看的云里雾里，还是algorithm流x，一讲便通环环相扣，吹爆！！！

balanced search tree延伸了binary search tree的逻辑，但添加了三个分支的节点，如下图，左边为小于E J的节点，中间为在E J中间的节点，右边为大于E J的节点，search方法与二分法逻辑相同，不多赘述



插入方法的逻辑为，每一次插入时都尽量的凑成三个分支的节点，如在H节点下插入I节点，则此节点变为H I节点，如果新插入的节点是插入到三个分支的节点上，则进行分裂，分裂方式如图所示

![1570537318651](Algorithms (forth edition) 笔记.assets/1570537318651.png)![1570537340159](Algorithms (forth edition) 笔记.assets/1570537340159.png)

基本的balanced search tree逻辑如上，而红黑树的逻辑则是基于balanced search tree进行

Red-black BSTs：

红黑树的逻辑，即为将balanced search tree中三个分支的节点，转化为红线链接的两个节点，

![1570537363309](Algorithms (forth edition) 笔记.assets/1570537363309.png)

在红黑树中插入有如下原则，即1）永远保持红线向左倾  2）一个节点有两条红线时会进行如balanced search tree中四个分支节点的分裂

![1570537379302](Algorithms (forth edition) 笔记.assets/1570537379302.png)

![1570537394136](Algorithms (forth edition) 笔记.assets/1570537394136.png)

因此在红黑树中插入时会常有较大的树形结构变化，如下图中Insert S中insert H的 步骤

![1570537410165](Algorithms (forth edition) 笔记.assets/1570537410165.png)

insert的H会在R下，且用红线链接，则有R此时与E链接，且R与E链接为红线，但此时红线为右倾，则转换红线的方向为左倾，完成变换

红黑树的长度不会超过2lgN

#### 4.Hashtable

了解hashtable的本质首先确定这是一种映射关系，我们将M个keys映射到N个index上，这个映射过程使用的是hash function，而每个index可能对应着多个keys，所以会产生搜索结果的冲突，要解决这种冲突，即需要collision-solution

hash fuction

基本的对应方式为hashcode()(M为hashtable中的index数量)

正整数取k%M，在0到1之间的浮点数则取k*M，然后取最接近这一结果的Index，字符串则采取特殊算法，其中R一般在java中为31![1570537427052](Algorithms (forth edition) 笔记.assets/1570537427052.png)

而合成的keys则是将每个部分分开计算hashcode

![1570537441013](Algorithms (forth edition) 笔记.assets/1570537441013.png)

hashcode最后再转换为Index很简单，直接与0x7fffffff做与运算即可（即去掉符号位的影响）

java对于基本的数据类型都有hashcode的方法（ `String`, `Integer`, `Double`, `Date`, and `URL`），其他类型的hashcode可自行定义，但需要有类似于.equals()的传递性

collsion-solution

两种基本的处理办法，一种为在每一个index中都添加一个链表，则搜索方法变为先搜索keys对应的index进入此链表，再在链表里面搜索keys

![1570537455943](Algorithms (forth edition) 笔记.assets/1570537455943.png)

另一种为取M个index（M大于keys的数量N），则如果一个index有了keys，将也对应这个Index的Keys往下接着放，则会有一个index下面临近几个index所储存的keys全部对应相同的index，因此搜索时会出现三种情况

1. 直接搜索到相应的key，search hit
2. 该index储存值为null，search miss
3. 该index储存不是相应keys，往下找直到找到或找不到相应keys

![1570537470042](Algorithms (forth edition) 笔记.assets/1570537470042.png)

### 图表：

#### 1.undirected graphs

基本的graph类型api如下

![1570172305955](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570172305955.png)

最重要的方法adj是一个链表的链表，数据结构如图所示

<img src="C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570172363027.png" alt="1570172363027" style="zoom: 50%;" />

undirected graph有两种搜索方法，depth first search搜索其中某一条从节点v能到节点s的路径，breadth-first search搜索最短的从节点v到节点s的路径

depth-first search主要有两个类

![1570172515591](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570172515591.png)

![1570172531799](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570172531799.png)

基本搜索逻辑为先从s节点递归式遍历一遍，遍历s节点的所有adj的节点，再遍历adj节点所有adj的节点，依次类推，每次遍历时将能够连接的节点marked，因此能够到达s节点的所有节点全部被marked，然后再去求这些节点到s节点的路径，求路径时每个节点有一个固定的edgeTo()方法，能返回一个指定的连接到该节点的节点，通过这样的顺序不断edgeTo(),直到从节点v到达节点s，因此中间的所有节点即为v到s的路径

breadth-first search

基本逻辑类似于depth-first search，先遍历一遍，然后每次与s相邻的节点都会marked，但breadth-first search是从s开始，能够通过一个edge直接到达s的edgeTo()的结果全为s，而与s相邻的节点再相邻的节点是通过两个edge到达s，则这些节点的edgeTo()的结果即全为与s距离为一个edge的节点，因此能够搜索到这些节点到s的最短距离

symbol graphs

对于一些节点名为string或其他形式的graph，一般采取如图的数据结构

![1570175749372](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570175749372.png)

#### 2.directed graphs

directed graph的逻辑基本类似于undirected graph,但图表多了方向，所以在进行DFS和BFS时需要根据顺序进行marked，即为沿着箭头方向不断marked，然后再来求其他节点是否有路径到源节点以及到源节点的最短路径。

cycle和DAGs(DAG为有向无环图表)

cycle detection很简单，同样运用DFS的逻辑，每次发散到一个节点即进行marked，如果出现该节点的下一轮节点已经被marked的时候，则出现了环

DAG有三种排列方法，即将逐渐mark的节点通过顺序展现出来，preoder——在递归开始之前进行添加进queue中，postorder——在递归完成后添加进queue中，reversePost——在递归完成后添加到stack中

![1570181414486](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570181414486.png)

*Topological sort*即使将DAG通过reversePost排序之后，会出现所有的edge指向都是从之前的节点指向之后的节点

![1570181537235](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570181537235.png)

Strong connectivity——可直接认为是undirect graph，因为每个节点之间的连接都是双向的

transive closure——一种形式的directed graph，但这种形式的directed graph即类似于右边的矩阵图，当且仅当原来的directed graph中节点v能够到达节点w时，这个transive closure才会有从v连接到w的edge

![1570185235461](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570185235461.png)

#### 3.minimum spanning trees

定义：minimum spanning trees是指的能够用最少的edge连接所有的节点的树

基本操作：cut和circle，cut是切断树中任何两个节点的连接，树将会变成两个分minimum spanning trees，circle是指的连接任何两个节点，树将会出现环

**Greedy MST algorithm**

将所有的节点想象成两方，黑线连接的节点始终在一方，其他没有连接的节点可自由分配，直到连接完所有的节点

![1570190933323](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570190933323.png)

当edge有不同的重量属性时，有如下的连接方式

**Prim's algorithm**

是从一个节点开始，每一次纳入一个新的节点，直到形成树

Prim's algorithm拥有两种连接方式，第一种为lazy implementation，第二种为eager implementation

<img src="C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570191081345.png" alt="1570191081345" style="zoom:50%;" />

lazy implementation即将所有的edge通过重量排序出来，已经连接在树中的节点之间不能再有edge,其他的节点连接即选择质量最小的edge来连接

![1570191246325](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570191246325.png)

eager implementation是修改lazy implementation，删除树中间节点之间的edge，同时因为每个节点添加时都是用的最小的连接，即直接选取该节点连接到树时最小重量的连接edge

![1570191562165](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570191562165.png)

**Kruskal's algorithm**

把所有节点之间的edge全都排序，选择重量最小的连接，同时删除树中节点的连接edge

![1570191616978](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570191616978.png)

#### 4.shortset paths

有向图表的最短路径即为有向图表的最小重量的路径，这一章的研究方法不是以及节点为重点，而是以edge为重点

![1570275499530](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570275499530.png)

求最短路径的api

![1570275560972](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570275560972.png)

基本数据形式为![1570275597184](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570275597184.png)

即edgeTo()是指从源节点到该点的最短edge，distTo()是从源节点到该点的最短路径，这里的逻辑基本为先计算源节点到距离一个edge节点的最短路径，此时有了第一批distTo()出现，然后再依次计算其他节点的distTo()

这里对于edge的操作为relaxation，即对于edge指向的点，如果直接的distTo[v]+e.weight<distTo[w],则将edgeTo[w]选择为这个e

![1570275839916](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570275839916.png)

所以对于节点进行relax操作即为遍历指向这个节点的所有edge，选择最轻的edge确定这一edgeTo()

![1570276585782](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570276585782.png)

**Dijkstra's algorithm**

这一算法的逻辑为先把所有的distTo()设为无穷，源节点自身的distTo()设为0，然后开始确定edgeTo()，同时确定distTo()，然后一直relax直到所有的点到源节点的距离全都确定。

**Acyclic edge-weighted digraphs**

这一算法是对于DAG即有向无环图的算法，基于有向无环图的拓扑排序实现，

*Single-source shortest paths problem in edge-weighted DAGs*（单源节点最短路径）

根据拓扑排序的顺序，一个接一个的对节点进行relax，然后就能求出其最短路径

*Single-source longest paths problem in edge-weighted DAGs*（单源节点最长路径）

方法同上，只需将每次relax的最短edge换成最长edge即可

*Critical path method*

这个方法中algorithm给了一个例子，即给定一连串的工作以及对应的工作时间，限制条件为有些工作必须在其他工作之前做完，求所有工作做完的最短时间。

![1570277109230](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570277109230.png)

这里的基本逻辑如下图，将所有工作的起点和终点都看作两个节点，然后中间的edge weight为时间（图中此edge为黑色），而有些工作一定要在其他工作之前完成，因此也有有向edge存在（图中此edge为红色），所有的关系形成之后即为下图没有s，t节点的样子。而这些工作是可以并列做的，因此可以将没有箭头指向的所有节点全都连接到s节点上，将所有没有箭头指出的节点全都连接到t节点上，此时也能保证所有的工作已做完，形成下图。

![1570277147129](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570277147129.png)

完成所有工作的最短时间即为s到t的最长路径。

![1570277773686](C:\Users\李甘霖\AppData\Roaming\Typora\typora-user-images\1570277773686.png)

