[[离散数学学习笔记]] 
>关键名词与重点算法辨析
# 绪论
## 名词辨析
- 数据data
- 数据对象data object
- 数据元素data element
- 数据项data item
- 数据结构 data structure相互之间存在关系的数据元素的集合
### 四大基本关系
>  (1) 集合 结构中的 如生 数据元素之间除了“同属千一个集合”的关系外，别无其他 关系气 (2) 线性结构 结构中的数据元素之间存在一个对 一个的关系； (3) 树形结构 结构中的数据元素之间存在一 个对多个的关系； (4) 图状结构或网状结构 结构中的数据 元素之间存在多个对多个的关系。图 1. 5 为上述 4 类基本 结构的关系图。由于“集合”是数据元素之间关系极为松散 的一种结构，因此也可用其他结构来表示它。

[[教材严蔚敏.pdf#page=15&selection=37,0,81,20|教材严蔚敏, 页面 15]]
- 集合
- 线性结构 一对一
- 树形结构 一对多
- 网状结构 多对多

   

# 树
## 名词辨析

孩子/父亲（双亲（严）)(parent)
祖先/后代
真祖先 真后代
深度/高度> 沿每个节点v到根r的唯一通路所经过边的数目，称作v 的深度（depth）[[教材邓俊辉.pdf#page=133&selection=26,3,35,0|教材邓俊辉, 页面 133]]
！严教材是用层次来定义的，随机应变即可
区别于图中的度，树中的度指的是孩子总数

## 关键算法
### 树，森林，二叉树的转化
关键理解长子兄弟表示法[[教材邓俊辉.pdf#page=135&selection=237,13,254,18|教材邓俊辉, 页面 135]]
![[森林与二叉树对应关系.png]]
把森林看作多叉树的子树集，自然可得到转化。

#### 多叉树，森林的遍历
结合例题[[样卷.pdf#page=2&selection=19,1,21,11|样卷, 页面 2]]
对于森林，先，中，后序与其二叉树一一对应
对于多叉树，先对应先，后对应中
### HUFFman树
其特点是只有二度节点和叶节点，因此设数量a，b，有等式 $边数=分叉数=2a=a+b-1=(3a+b-1)/2=2(b-1)$






# 图
## 名词辨析
- 连通分量 极大连通子图 所谓极大即添加任意的vertex不连通
- 强/弱连通图 强弱的概念是对于有向图来说的，弱连通是其对应的无向图连通
- 生成树/支撑树 是对于连通图来说的，极小连通子图，再去掉任何一条边就不连通，边数n-1
- 邻接表 分为头节点数组和表节点![[Pasted image 20250605164835.png]]
- 逆邻接表 针对有向图，顾名思义，便于计算入度
- 十字链表针对有向图，相当于结合了上两个图![[Pasted image 20250605165144.png]]
- 邻接多重表 针对无向图，参考十字链表![[Pasted image 20250605165608.png]]![[Pasted image 20250605165634.png]]
## 关键算法
### 遍历算法
BFS DFS 及dfs bfs tree forest
### 最小生成树
#### prim算法 O(n^2)
> 可基于贪心策略导出一个迭代式算法。每一步迭代之前，假设已经得到最小支 撑树T的一棵子树Tk = (Vk; Ek)，其中Vk包含k个顶点，Ek包含k - 1条边。于是，若将Vk及其补 集视作原图的一个割，则在找到该割的最短跨越边ek = (vk, uk)（vkVk且ukVk）之后，即可 将Tk扩展为一棵更大的子树Tk+1 = (Vk+1; Ek+1)，其中Vk+1 = Vk  {uk}，Ek+1 = Ek  {ek}。 最初的T1不含边而仅含单个顶点，故可从原图的顶点中任意选取。

[[教材邓俊辉.pdf#page=198&selection=132,5,242,1|教材邓俊辉, 页面 198]]
#### kruskai算法O(eloge) 特别适合稀疏图

从无边的孤立点出发，加n条边，每次选最小边
### 有向无环图（类似于偏序图）
#### 拓扑排序
#### 关键路径（AOE activity on edge）
1. 在拓扑排序的过程中递推获得每个节点的最早发生时间，最早发生时间是开始点到该点的最大长度
2. 在逆拓扑（栈实现）过程中递推获得每个节点最晚发生时间，最晚发生时间是总长度减去结束点到该点的最短路（完成点一定是关键，最早最晚相等）
3. 根据弧与节点关系求得每个弧的两个值，比较得到关键路径
### 最短路径
#### dijkstra算法
#### floyd算法
两种算法时间复杂度无区别，进行n次dijstra算法等效于floyd
# 查找
## 概念辨析
- ASL average search length 等于查找概率与查找长度乘积之和
- 动态查找表 如BST，其结构是在查找过程中动态生成的，插入，删除
## 关键算法
### BST(binary search tree)二叉查找树/二叉搜索树家族
#### 左右都不为空情况下删除节点方法

![[Pasted image 20250605212809.png]]
> 解释，方法一利用的是二叉排序树右子树大于根大于左子树的特性；方法二利用直接前驱后继一定只有一个或没有子树，如果有的话，往下延伸一定能继续逼近，矛盾。

#### AVL树(平衡二叉搜索树)

> 由G. M. Adelson-Velsky和E. M. Landis不1962年収明[36]，幵以他们名字的首字母命名

[[教材邓俊辉.pdf#page=216&selection=390,0,401,3|教材邓俊辉, 页面 216]]
[avl树动态演示](https://www.cs.usfca.edu/~galles/visualization/AVLtree.html)
根据插入/删除后的形态，一定能在两次旋转（单旋/双旋）以内恢复其平衡
##### 统一重平衡算法
找到最低失衡点，孩子节点，孙子节点，中序排序，对应的子树中序排序重组起来（省略中间步骤）
### 哈希表/散列表
[散列表维基百科](https://zh.wikipedia.org/zh-cn/%E5%93%88%E5%B8%8C%E8%A1%A8)
> 1. 已知一组关键字(30,1,12,25,33,55,11,71,8)，哈希函数为：H(key)=key % 8, 哈希表 HT[0..7]，采 用链地址（尾插法）处理冲突。（共 6 分） 1）按照顺序先后存入关键字元素，画出存储所有元素后的哈希表 HT； 2）计算查找成功和失败时的平均查找长度 ASL。

[[B卷(2).pdf#page=4&selection=63,0,91,1|B卷(2), 页面 4]]
- 函数构造
- 处理冲突
#### 查找分析
> 定的哈希函数是均匀的，则可不考虑它对平均查找长度的影响。 对同样一组关键字，设定相同的哈希函数，则不同的处理冲突的方法得到的哈希表不 同，它们的平均查找长度也不同。如例 9-3 和例 9-4 中的两个哈希表，在记录的查找概率 相等的前提下，前者（链地址法）的平均查找长度为 ASL(12) =一 (1• 6 + 2• 4 + 3 + 4) = 1. 75 12 后者（线性探测再散列）的平均查找长度为 ASL(12) =一 (1• 6 + 2 + 3• 3 + 4 + 9) = 2. 5

[[教材严蔚敏.pdf#page=270&selection=269,2,327,4|教材严蔚敏, 页面 270]]


# 排序
[十大经典排序算法-菜鸟教程](https://www.runoob.com/w3cnote/ten-sorting-algorithm.html)
![[十大排序算法总结.png]]
## 按时间复杂度分类归纳
- $n^2$ :三种  冒泡 插入（扑克牌）选择（反复选择最小的）
- $nlogn$：四种 希尔（插入排序的改进）归并 快速 堆
- 基数排序
