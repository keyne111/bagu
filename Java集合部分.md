# java集合（上）

## Java集合概览

Java集合，也叫容器，主要有两大接口派生而来，一个是Collection接口，用于存放单一元素，另一个是Map接口，用于存储键值对，Collection接口下面有三个主要的子接口，List,Set,Queue



## 说说List,Set,Queue,Map的区别？

List存储的元素是有序，可重复的，可以存多个null值，元素可以通过索引访问

Set存储的元素是无序，不可重复的，只能存一个null值，set集合只能通过元素本身去访问

Queue主要是按照特定的规则去排序的，存储的元素也是有序可重复的

Map存储的是键值对，key是无序，不可重复，value的话无序可重复，每个key最多映射一个value



## Collection下面的集合

List:

ArrayList:Object[]数组实现

Vector:Object[]数组实现

LinkedList:双向链表，（JDK1.6之前是循环链表，1.7取消了循环）



Set:

HashSet:无序，唯一，基于HashMap实现，底层也是用HashMap存储

LinkedHashSet:是HashSet的子类，底层基于LinkedHashMap实现

TreeSet:有序，唯一，红黑树



Queue:

PriorityQueue:Object[]数组实现小顶堆

DelayQueue:底层基于PriorityQueue实现

ArrayDeque:可扩容动态双向数组



## Map下面的集合

HashMap:在JDK1.8之前主要由数组+链表组成，数组是HashMap的主体，链表是为了解决哈希冲突的。在1.8之后有了改变，当链表长度大于阈值时（阈值默认是8），会将链表转换成红黑树，减少搜索时间，不过在转成红黑树之前，还会对数组长度比较，看看是不是小于64，如果小于64，会先对数组进行扩容，再转成红黑树

LinkedHashMap:继承HashMap,底层也是数组+链表或红黑树组成，不过它新增了一条双向链表，可以确定键值对的插入顺序，实现访问顺序相关逻辑

HashTable:也是数组+链表，数组也是HashTable的主体，链表解决哈希冲突用的

TreeMap:与红黑树相关



## 如何选用集合？

根据集合的特点去选

比如如果需要键值对，我们就选Map相关的接口，如果需要排序的，选TreeMap,不需要排序的就选HashMap,线程安全的就选ConcurrentHashMap

如果需要存储单一元素，选Collection下的接口，像唯一性，选Set相关，需要有序的就选TreeSet,无序的就选HashSet



## 为什么要使用集合？

当我们想要存储一组数据类型相同的数据时，数组是最基本最常用的容器之一，但是它也存在一些不足，因为在实际开发中，我们需要存储的对象是多种多样且==数量不确定的==，而Java集合框架中可以存储各种数据类型和不定数量，而且相比于数组，它大小可变，支持泛型，具有内建算法，提高了对数据的存储和灵活性。提高我们开发程序的效率



## ArrayList和Array(数组) 有什么区别？

ArrayList是动态数组，Array是静态数组，前者使用起来更方便和灵活。

ArrayList创建时不需要指定大小，数组创建时需要指定大小

ArrayList可以根据存储的元素动态地扩容或缩容，数组在创建后就不能修改长度了

ArrayList支持泛型，数组不支持

==ArrayList中存放的是对象和包装类型，数组存放的是对象和基本类型==

ArrayList有丰富的API操作元素，数组只能通过索引访问和遍历元素，其它操作需要自己手动执行

### ArrayList(底层原理):

![image-20240922200125817](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922200125817.png)

## ArrayList 和 Vector的区别 （了解）

ArrayList是List的主要实现类，底层使用Object[] 实现，适用于频繁查找，线程不安全

Vector是List的古老实现类，底层也是用Object[]实现，线程安全



## Vector 和 Stack 的区别 （了解）

Vector 和 Stack都是线程安全的，都基于sycnhoizd 关键字同步处理

Stack继承Vector ，它是一个后进先出的栈， Vector是一个列表

但是这两个已经很少用了，在高并发场景下通常用的ConcurrentHashMap 和CopyOnWriteArrayList  或者手动实现线程方法去实现



## ArrayList中可以添加null值吗？

ArrayList可以添加任何类型的数据，包括null值，但是不建议在ArrayList中添加null，因为这会让代码难以维护，比如不做判空处理会导致空指针



## ArrayList插入和删除的时间复杂度

从头部插入的话：因为所有元素都要往后移一位，所以是O(n)

从尾部插入的话：不需要移动元素，O(1)

从指定位置插入的话：插入位置之后的元素都需要往后移一位，相当于需要移动二分之n个元素，时间复杂度也是O(n)



删除的话和插入的时间复杂度一样，不过原理是删除之后的元素都需要往前移动而已



## LinkedList插入和删除的时间复杂度

头部插入/删除  O(1)

尾部插入/删除 O（1）

在指定位置：先遍历找到要修改的元素，再去移动要修改的节点前后节点的指针。平均需要遍历二分之n个元素，O（n）



## LinkedList为什么不能实现RandomAccess接口？

实现RandomAccess接口可以通过索引快速访问元素，而LinkedList底层是链表，内存地址不连续，只能通过指针定位，不支持通过索引访问元素

## ArrayList与LinkedList的区别？

1：线程安全：ArrayList与LinkedList都是不同步的，线程都不安全

2：底层数据结构：ArrayList用Object[]数组存储，LinkedList是双向链表（JDK1.6之前是循环链表，1.7取消了循环）

3：插入和删除方面：ArrayList的插入和删除麻烦，但查询简单，而LinkedList是插入和删除简单，查询麻烦

4：快速访问：ArrayList因为实现了RandomAccess接口，支持索引快速访问元素，而LinkedList底层是链表，内存地址不连续，不支持索引快速访问元素

5：内存：ArrayList会在数组的最后预留一定的容量存储，LinkedList会在每个元素前驱和后继消耗容量，每一个元素比ArrayList消耗更多的容量



## ==ArrayList的扩容机制是什么？==

会先计算出要扩容的数组的长度，默认是1.5倍，然后把原来数组的数据搬迁到扩容后的数组的里面，然后更新原来数组的地址引用。然后如果扩容后还是放不下的话， 那就以实际数组长度为准

==它是依靠的是内部的ensureCapacity操作，它会先判断数组是否需要扩容，需要扩容的话就调用grow（）方法去实际执行这个操作==



## Set集合中Comparable接口和Comparator接口区别？

它们都是Set集合中用于排序的接口，在比较类对象大小，排序方面发挥了作用

Comparable有一个compareTo方法

Comparator有一个compare方法

当我们需要对一个集合进行排序，可以重写compareTo或compare方法

当我们需要对一个集合进行两种排序，可以重写compareTo方法和使用自定义的comparator方法，或者使用两个自定义的comparator方法

## Set集合中无序性和不可重复性指的是什么？

无序性不是随机性，它是指元素在底层数组中的存储方式，不是按照，数组的索引顺序添加的，而是由元素的哈希值决定的

不可重复性：set集合中的元素不能重复，利用equals方法比较，如果equals方法相等，则元素重复



## 说说HashSet,LinkedHashSet,TreeSet的异同？

相同点：它们都是Set集合的实现类，都能保证元素的顺序唯一，都线程不安全。

区别：它们主要的区别是底层的数据结构不同

HashSet底层是HashMap,适用于对插入顺序和取出顺序不要求的场景

LinkedHashSet底层是LinkedHashMap，适用于对插入顺序和取出顺序满足FIFO（先进先出）的场景

TreeSet底层是红黑树。 适用于自定义排序的场景

## Queue与Deque的区别？

Queue是单向队列，只能一端插入，另一端删除，实现了Collection接口，遵循先进先出 (FIFO)的规则,根据由于容量问题而导致操作失败的处理结果分为两类，一类是抛出异常，另一类是返回特殊值

Deque实现了Queue接口，也是处理结果分为两类，增加了在队首和队尾插入和删除的方法，还提供pop方法和push方法，可以用于模拟栈



## ArrayDeque和LinkedList的区别？

首先，它们都实现了Queue接口，都具有队列的功能

ArrayDeque是基于可变长的数组+双指针实现的，LinkedList基于链表实现

ArrayDeque不允许添加null数据，LinkedList支持

ArrayDeque是在JDK1.6推出的，LinkedList在JDK1.2就有了

ArrayDeque在插入数据时可能存在扩容操作，均摊后时间复杂度是O(1)，LinkedList不需要扩容，但是在插入数据时需要申请一个新的堆空间，均摊后性能更低

所以，在实现队列方面，更适合使用ArrayDeque，它也可以用于模拟栈



## 下面还有四个问题 可是我见都没见过的东西。暂时就不背了

### [说一说 PriorityQueue]

### [什么是 BlockingQueue？]

### [BlockingQueue 的实现类有哪些？]

### [ArrayBlockingQueue 和 LinkedBlockingQueue 有什么区别？]



# java集合（下）

## HashMap与HashTable之间的区别？

总共有6个区别。

1：线程安全方面：HashMap线程不安全，HashTable线程安全，因为它内部的方法都经过syhonized关键字修饰

==2：效率：因为线程不安全，所以HashMap比HashTable快==

3：null key和null value：HashMap可以允许null key和null value，key只能有一个，value可以有多个，HashTable不支持

4：初始容量和扩充容量方面：在没有初始值的情况下，HashTable的初始容量为11，扩充容量为2n+1,HashMap的初始容量为16，扩充容量为2n,有初始值的情况下，HashTable的初始容量为初始值，HashMap的初始容量为2的幂次方大小

5：底层数据结构：JDK1.8之后，HashMap的链表到达阈值（默认是8）后会转成红黑树，减少搜索数据，HashTable不行

6：哈希函数：HashMap的哈希值是高位与低位的混合处理去解决冲突，而HashTable的哈希值是hashCode的值



## HashMap与HashSet的区别？

HashMap实现了Map接口，存储键值对， HashSet实现Set接口，存储单一元素

HashMap使用put方法添加元素，  			HashSet使用add方法添加元素

HashMap使用key计算hashCode,				HashSet使用成员对象计算hashCode



## HashMap与TreeMap的区别？

它们都继承AbstractMap，不过TreeMap还实现了NavigableMap和SortedMap,所以有了对集合中的元素搜索的能力和根据集合中的key排序的能力



## HashSet如何检查重复？

先计算对象的hashcode值，如果不相等，那就直接插入，相等的话再比较一下equals方法，因为object的equals方法是比较内存地址的，内存地址不相等的话，就可以插入了

不过在jdk1.8的时候，它的add()方法，不管有没有重复对象，HashSet都会直接插入，不过add方法的返回值会返回插入之前是否相等而已。



## HashMap的底层实现？

JDK1.8之前，HashMap由数组+链表组成，数组是HashMap的主体，链表主要是用来解决哈希冲突用的（拉链法，创建一个链表数组，计算元素的哈希值，不冲突的话加直接插入，冲突的话就加到链表后面）

JDK1.8，HashMap由数组+链表和红黑树组成，当链表长度小于阈值时（默认是8），会将链表转成红黑树，减少搜索时间，不过如果数组长度<64,会先进行数组扩容再转成红黑树



## 为什么HashMap的长度是2的幂次方？

因为哈希值的范围太大，内存放不下，我们可以想到通过对数组的长度进行求余操作得到元素的存放位置，然后如果hashmap的长度是2的幂次方的话，求余操作可以等价于数组的长度-1  & hash，&操作的性能比%操作性能好，更快计算元素的存放位置。



## HashMap多线程导致死循环？

JDK1.7及之前的HashMap在多线程环境下容易导致死循环，因为一个桶位中的多个元素想要扩容时，多个线程对链表进行操作，头插法可能导致链表中的节点出错，让链表变成环形链表。

在JDK1.8中，改进了头插法，变成尾插法，链表不会变成环形链表了，不过因为HashMap线程不安全，不建议使用它，在高并发下使用ConCurrentHashMap比较好



## HashMap为什么线程不安全？

JDK1.7之前，多线程环境下，hashMap进行扩容操作会造成死循环和数据丢失的风险

JDK1.8，多个键值对可能被存放在同一个桶中，它们被存放在链表或红黑树里，多线程情况下执行put操作，可能会造成数据覆盖。

## HashMap常见的遍历方式及性能？

迭代器EntrySet

迭代器keySet

forEach EntrySet

forEach KeySet

Lambda

StramApi单线程

StreamApi多线程

存在阻塞时parallelStream性能最高，不存在阻塞时parallelStream性能最差



## ConcurrentHashMap与HashTable的区别？

它们主要是实现线程安全的方式不同。

从底层数据结构来看：

ConcurrentHashMap在JDK1.7的时候是分段的数组+链表 ，在JDK1.8的时候是数组+链表或红黑树

而HashTable的底层数据结构一直是数组+链表，数组是它的主体，链表用于解决哈希冲突

从实现线程安全的角度来看：

ConcurrentHashMap在JDK1.7是使用分段锁，锁住容器数据，多线程访问不同数据段的容器数据，不会造成线程冲突，在JDK1.8的时候，优化成使用synchronized关键字和CAS操作

而HashTable实现线程安全则是使用synchronized 关键字修饰，当多线程访问同一个方法时，进入阻塞和轮询状态，效率较差



## ConcurrentHashMap为什么不允许使用将key和value作为null？

因为将key和value作为null会产生歧义，比如说这个null究竟有没存在于集合，还是说返回的结果就是null

然后单线程下可以容忍歧义，但是多线程下不能容忍，因为无法正确判定键值对是否存在（在其它线程做了修改的情况下）



## ConcurrentHashMap可以保证复合操作的原子性吗？

无法保证，因为线程可能在执行过程中被另一个线程中断，导致结果不和预期结果一致。

然后如果想保证复合操作的原子性的话，可以选择ConcurrentHashMap提供的一些API，它有做操作保证复合操作的原子性，或者也可以选择synchronized关键字，不过这个不推荐就是了