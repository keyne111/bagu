stream是什么？

==流只能收集一次==

对数据进行操作的东西，和Collection类的区别是stream是做计算的，Collection类是做筛选阿，过滤之类的

为什么要用stream？

方便我们简化数据计算的操作

定义stram流的方法(常用)

集合：  对象.stream()

==map集合不能直接调用stream()方法的==

```
Map<String,Double> map=new HashMap<>();
map.entrySet().stream()
```



数组:	Arrays.stream()

无数据要自己去构造的: Stream.of()



筛选与切片

==limit(个数) ：截取多少个元素==

==filter(对象 -> 过滤条件)==

==skip(个数)  :跳过筛选出来的几个元素==

==distinct() :去重的==

映射：

==map(对象->对象体)   for循环访问集合，return里面的结果==

flatMap相当于把[1,2,3,[4,5,6]]简化为[1,2,3,4,5,6]的操作



排序：

==sorted()： 自然排序，从小到大排序==

==sorted(Compator com):定制排序==



终止操作

allMatch

anyMatch

noneMatch

findFirst

findAny

==max==

==min==

==forEach()：这个感觉和中间操作的map很像==

==count==

规约：

reduce（初始值，类似条件的东西）

reduce（直接放条件）



收集：

==collect ：感觉主要作用就是转成不同的数据类型，经常用Collectors.toList()==，

==Collectors.toMap(s->s.getId,s-> s)//把s对象的id作为键，s对象作为值==





Optional:为了在程序中避免出现空指针异常而创建的

ofNullable(T t) 允许里面的东西是空指针

ofElse(T t) 如果对象没有赋值的话，使用这个T t作为默认对象



## Stream流

==流只能收集一次==

map集合不能直接调用stream()方法的

```
Map<String,Double> map=new HashMap<>();
map.entrySet().stream();
```

![image-20240923165142105](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923165142105.png)

![image-20240923171610402](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923171610402.png)

![image-20240923171731314](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923171731314.png)

终结方法

![image-20240923171834097](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923171834097.png)

### ==收集stream流==

![image-20240923172832161](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923172832161.png)

==collect转成map相关的==

```
Map<String, Student> collect = students.stream()
        .filter(s -> s.getHeight() > 170)
        .distinct()
        .collect(Collectors.toMap(a -> a.getName(), a -> a));
collect.forEach((k,v)-> System.out.println(k+"-->"+v));
//
蜘蛛精-->Student{name='蜘蛛精', age=26, height=172.5}
牛魔王-->Student{name='牛魔王', age=35, height=183.3}
```



把stream流转成数组，

![image-20240923173518869](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923173518869.png)