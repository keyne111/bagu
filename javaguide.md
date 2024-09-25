



# Java基础（上）

## ==java语言有什么特点？==

1：简单易学

2：面向对象（封装，继承，多态）

3：跨平台性（Java虚拟机实现平台无关性）

4：可靠性（Java具有异常处理机制和自动内存管理机制）

5：内置多线程（像C++没有内置多线程，要用操作系统的多线程功能实现，而Java内置了多线程）

6：安全性（Java语言的设计就提供了多重安全防护机制如访问权限修饰符，限制程序直接访问操作系统资源）

7：高效性（有Just in time等编译器的优化，Java的执行效率不错）

8：支持网络编程并且很方便

9：编译与解释共存

## JAVASE与JAVAEE

JAVASE:基础技术

JAVAEE:企业解决方案的技术

JAVAME:微型应用的技术，市场反馈不行



## JVM&&JDK&&JRE

JVM，是Java虚拟机，是运行字节码文件的虚拟机，它有针对不同系统的特定实现，目的是使用相同的字节码文件，在不同的操作系统下给出相同的结果，字节码文件和不同系统的JVM是Java语言“一次编译，随处可以执行”的关键



JRE包含Java运行时环境（JVM）和必要的类库， JDK包含了JRE和像JavaC,javadoc等工具



JVM是Java虚拟机，Java程序（.java）文件经过javac编译器成功后生成.class文件，Java把文件放到JVM执行，这个文件被Java虚拟机执行后就生成了我们所看到的结果。Java自己写好的程序是放在核心类库上面的



## 什么是字节码？采用字节码文件的好处是什么？

JVM可以理解的代码就是字节码，即.class文件，采用字节码文件好处

1：在一定程度上解决了传统解释型语言执行效率低的问题，保留了解释型语言可移植性的特点，==所以运行时相对高效==

2：一次编译，随处可以执行

## 为什么说Java语言编译与解释共存?

首先，编译型语言是一次性把代码翻译成机器码再执行，这样的话执行速度快，开发效率低，像C，C++就是编译型语言

​	而解释型语言是边解释边执行，这样的话是开发效率快，执行速度慢，像python，JavaScript就是解释型语言

然后Java语言既具有编译性语言的特点，又具有解释型语言的特点，Java语言是先编译，后解释，先把Java程序编译成.class文件,又通过Java解释器或JIT编译器进行解释



## JAVA和C++的区别?

JAVA与c++都是面向对象,都具有封装,继承,多态,

但是1:Java没有指针直接访问内存,程序内存更加安全

​	2:Java的类是单继承,C++支持多重继承,虽然Java的类不可以多继承,但是接口可以多继承

​	3:C++具有方法重载和操作符重载,Java只支持方法重载,因为操作符重载太复杂,与最开始要设计的思路简单不合.

​	4:Java有自动内存管理垃圾回收机制(GC),程序员无需手动释放无用内存



## 注释有哪几种?

单行注释

多行注释

文档注释

特点：给程序员理解程序用的。



## 标识符和关键字区别?

标识符就是用来起名字的,给类,方法,变量等,组成是以数字,字母,下划线_或美元符号$,然后不能以数字开头,也不能是关键字去命名

关键字就是被赋予了特殊意义的标识符,比如private,class之类,然后注意下关键字都是小写开头的,

true,false,null看起来像关键字,但是他们实际上是字面值,但是也不能作为标识符使用



## 自增自减运算符

b=a++ ,b=a ,a=a+1  

b=++a b=a+1,a=a+1

第一种情况：

```
int c= 10;
int d = 5;
int rs3=c++ + ++c - --d - ++d +1 + c--;
System.out.println(rs3); //26
System.out.println(c);	//11
System.out.println(d);	//5
```

另一种特殊的情况：

```
int a=2;
a=a++; //a是先存进操作上堆栈，+1操作，再把值赋给a
System.out.println(a); //2

int a=2;
a+=a++;
System.out.println(a);//4
```

[Java千问：学透Java自增(++)自减(--)运算符，看这一篇就够了！_java ++-CSDN博客](https://blog.csdn.net/shalimu/article/details/104039437#:~:text=Java自增和自减运)

## 移位运算符

左移<<,高位丢弃，低位补0，有时候相当于乘2，但是有时可能变成符号相反，正数变负数，还有一种情况，比如int是32位的，你左移32位，要先对32位求余，再进行左移

带符号右移>>，分两种情况，正数右移和负数右移，正数右移是低位丢弃，高位补0，负数右移是先求补码，低位丢弃，高位补1，然后按位取反+1才得到结果

无符号右移>>>，正数：低位丢弃，高位补0，负数：先求补码再低位丢弃，高位补0

double和float两种不能进行移位，移位运算符支持的只有int和long类型,其它类型如short，byte，char会转成int再操作,

超过位数的话会先对数进行求余在移位,如int对32求余,float对64求余



## continue,break,return的区别?

continue:跳出这次循环,进入下一次循环

break:中止循环,执行循环下面的语句

return:两种用法,1:return;不带返回值终止程序

​							 2:return value;带返回值终止程序



## Java中的基本数据类型

4大类，8种类型  后面的数字是占据的内存

整形(byte,short,int,long) 1,2,4,8

浮点型(float,double)	4,8	

字符型(char)	2

布尔型(boolean)	1



byte，

short，

int，

long (默认值 oL),使用long型时，如果不加L会作为int类型去编译

float（默认值 0f），数值后必须加f或F，否则编译失败，==因为浮点型默认是作为double编译的==

double（默认值 0d）

char

boolean （false）

它们的包装类型除了int和char是Integer和Character,其它都是首字母大写



## ==基本类型和包装类型的区别?==

1:用途:除了常量和局部变量之外,在其它地方比如方法参数,==对象属性==很少使用基本类型,并且包装类型可以作为泛型,基本类型不行

2:存储方式:基本类型的局部变量存储在Java虚拟机栈中的局部变量表中,(未被static修饰的)成员变量存储在Java虚拟机堆中,被static修饰的成员变量也存放在堆中，但属于类，不属于对象，而包装类型属于对象类型,几乎所有对象实例都是存储在堆中

**局部变量：在方法、构造函数或代码块（如`for`循环、`if`语句块等）内部定义的变量。**

**成员变量：成员变量是在类的内部、方法之外定义的变量。它们可以是类的字段，也可以是实例的字段。**

3:占用空间:相比较与包装类型,基本类型的占用空间往往非常小

==4:默认值==: ==基本类型的成员变量不赋初值有对应类型的默认值,包装类型的成员变量的话不赋初值是null。而局部变量不赋初值打印的时候会有提示警告==

==5:比较方式:基本类型的值比较方式是用======  ,而包装类型用======比较的是内存地址,要想比较包装类型的值的话,得用equals()方法==



为什么几乎所有对象实例都存放于堆中？

因为HotSpot虚拟机引入了JIT优化后，会对对象进行逃逸分析，如果发现某一个对象没有逃逸到方法外部，可能会用标量替换的方法实现栈上分配，避免堆中分配内存



## 包装类型的缓存机制了解吗?

包装类型大部分都使用了缓存机制提升性能,

比如Byte,Short,Integer,Long 这四个创建了[-128,127]范围内的数值,Chracter创建的[0,127]范围内的,Boolean类型返回的true或false,Float类型和Double类型则没有使用缓存机制,

只要在这部分范围内的数值,都是使用缓存中的对象,不然就是创建一个新的对象,但是要注意虽然两个数值都是缓存中的对象,只有数值相等才会缓存成同一个对象,不然就是缓存成不同的对象

```java
Integer i1 = 40; //使用缓存中的对象
Integer i2 = new Integer(40); //在堆上重新创建一个对象
System.out.println(i1==i2);
```

Integer i1=40;

它等于Integer i1=Integer.valueOf(40)



## 自动装箱与自动拆箱了解吗?原理是什么?

装箱:把基本类型变成包装类型 Integer i=1;  等价于 Integer i=Integer.valueOf(1);

拆箱:把包装类型变成基本类型 int j=i;            等价于int j=i.intValue();

装箱利用了valueOf()方法

拆箱利用了xxxValue()方法

==然后要注意不能频繁拆装箱,很影响系统性能==



## 为什么浮点数运算会有精度丢失的风险?如何解决浮点数运算的精度丢失问题?

这个和计算机保存浮点数的机制有关,因为计算机是二进制的,然后如果遇到无限循环的小数的话,因为宽度有限,只能进行截断操作,所以存在精度丢失的风险.

解决问题的话可以使用一个Bigdecimal,他不会造成精度丢失,然后在一些业务场景,比如涉及钱的,经常使用这个Bigdecimal



Bigdecimal，使用字符串的构造方法才不会精度问题，因为底层是把字符串转成数组了，比如0.1  ，在数组中0存一位  .存一位  1存一位  { "0" , "." , "1"}

==用String类型的参数入参，或者静态方法的valueOf  把double转成Bigdecimal,才能正确解决精度丢失==

## 超过long整形的数据如何表示?

BigInteger,它内部使用的int[]数组来表示任意大小的整数数据,但是他相对于正常整数类型的运算来说的话,它的运算效率相对低



## ==成员变量与局部变量的区别？==

1：语法形式：成员变量是属于类的，==而局部变量是代码块或方法内定义的变量或方法的参数====，然后成员变量可以被private,public,static等修饰符修饰，局部变量不行，但是他们都能被final修饰==

2：存储方式上：基本类型的局部变量是存放在Java虚拟机栈中的局部变量表中的，而未被static修饰的成员变量属于Java虚拟机堆中，被static修饰的成员变量属于堆中，不过它属于对象，不属于实例

==3：生存时间：成员变量是对象的一部分，成员变量随着对象的创建而创建，局部变量的生存时间是随着方法调用而创建，随着方法调用结束而消亡==

==4：默认值：基本类型的成员变量不赋初值有对应类型的默认值,包装类型的成员变量的话不赋初值是null。而局部变量不赋初值打印的时候会有提示警告==



## 为什么成员变量有默认值？局部变量没有默认值？

首先，变量存储的是内存地址对应的随机任意值，如果没有默认值，程序读取该值运行时会出现意外

然后默认值有两种赋值方法：手动和自动，成员变量可以通过反射等方法为变量手动赋值，而局部变量不行

编译器（javac）通过检查，发现局部变量没赋值，可以直接报错，但是成员变量不行，它可能是运行时通过反射赋值，对成员变量处于一种报错不行，不报错又可能没赋值，于是自动赋默认值



## 静态变量有什么作用？

静态变量是被static修饰的变量，通过类名.变量使用，然后无论一个类创建了多少个对象，静态变量只会被分配一次内存，这样可以节省内存，通常情况下，静态变量会被final修饰成常量



## 字符型常量和字符串常量的区别？

1：形式：字符型常量是用单引号括起来的单个字符，字符串常量是用双引号括起来的0个或多个字符

2：含义：字符型常量相当于一个ASCII值，可以参与表达式运算，字符串常量代表一个地址值

3：内存：字符型常量占两个字节，字符串常量占若干个字节

==字符型常量里面可以是空格，'(空格)'==

必须有仅且只有一个，不然编译报错

## 什么是方法的返回值？方法有哪几种类型？

方法体中的代码执行后产生的结果，如果有返回值的话，返回值的作用是接收结果，让它用于其它操作

按照方法的参数和返回值分：

方法有四种类型，无参无返回值，无参有返回值，有参无返，有参有返



## 静态方法为什么不能调用非静态成员？

静态方法是属于类的，在类加载的时候分配内存，此时就可以通过类名.方法调用了，而非静态成员变量是属于对象实例的，需要在对象实例化之后才能调用它，也就是说静态方法存在的时候非静态成员还没出生，这样去调用是非法操作，会报错



## 静态方法和实例方法（普通方法）有什么不同？

1：调用方式不同，静态方法可以使用类名.方法去使用，也可以使用对象.方法去使用，而实例方法只有对象.方法去使用，然后静态方法是属于类的，尽量不要用对象.方法去调用，容易造成混淆，也就是说静态方法可以无需创建对象

2：访问类成员变量的限制：静态方法不允许访问非静态成员变量和非静态方法，可以访问静态成员变量和静态成员方法，然后实例方法就没有这个限制

3：静态方法中不能出现this关键字，实例方法中可以出现（还是出现时间的问题）

## ==工具类的方法为什么要用静态方法创建而不是实例方法创建？==

因为我们只需要使用里面的方法就可以，用实例方法创建的话需要创建对象，但是创建对象是需要消耗内存的，用实例方法就可以解决这个问题

## 

## 方法重载和方法重写有什么不同？

重载：同个类中（或者父类和子类之间）方法名相同，根据输入数据的不同，返回不同的处理

重写：子类继承父类的相同方法，输入相同的数据，返回不同的响应

具体来说，重载就是要求方法名相同，然后参数数量，参数类型，参数顺序有一个不同，就是方法重载，跟方法的返回值和访问权限修饰符无关，方法重载可以重载任何方法。

重写呢，就是子类继承父亲的相同方法，然后有两同两小一大的要求

方法名和参数类别相同

返回值小于或等于父类方法的返回值，异常也是小于或等于父类方法的异常

访问权限修饰符大于或等于父类的访问权限修饰符

==注意父类的构造方法和被private，final，static修饰的方法都不能重写==，还有父类返回值是void和null的话，子类也是一样，父类如果是引用类型的话，子类可以返回该引用类型的子类



## 什么是可变长参数？

调用方法时可以传入不定数量的参数作为参数值，定义的话是类型...，然后需要注意的是它只能写在参数列表的最后，只有单它一个可变长参数时才写在前面，

最后的话遇到方法重载的时候，会优先匹配固定参数的函数而不是有可变长参数的函数，还有==它被编译后实际上是变成了数组的==



# Java基础（中）

## 面向对象和面向过程的区别？

解决问题的方式不同

==面向对象是抽取出对象，然后用对象执行方法解决问题==

==面向过程是把解决问题的过程拆成一个个方法，利用一个个的方法执行解决问题==

==面向对象开发的程序一般易维护，易扩展，易复用==



## 创建一个对象用什么运算符？对象实体和对象引用区别？

new运算符，new对象实例（存放在堆中），对象引用指向对象实例（对象引用存放在栈内存中）

一个对象引用有0或1个对象

一个对象可以被n个引用指向



## 对象的相等和引用相等的区别？

对象的相等是比较内存中存放的内容是否相等，用equals()方法

引用相等是比较指向的内存地址是否相等，用==比较



## 如果一个类没有声明构造方法，程序还能执行下去吗？

首先，构造方法作用是用于完成对象的初始化工作的，如果没有声明的话，它会默认生成一个无参的构造方法，程序可以继续执行下去，如果有自己有重载有参的构造方法的话，最好把无参的构造方法也写上去，这样可以在创建对象的时候少踩坑。



## 构造方法有哪些特点？是否可被override(重写)

方法名和类名一样，无返回值，且不能用void声明构造方法，==在new对象的时候自动执行，无需手动调用，==

它不能被override（重写），但是可以被overload(重载)



## 面向对象三大特征？

封装，继承，多态

封装就是把一个对象的状态信息隐藏在对象内部，外部不能直接访问对象的内部信息，但是可以提供让外界访问的方法，就像使用空调，我们不知道空调内部的零件，但是我们可以通过遥控器使用空调，然后属性要是不想被访问，就不要提供给外界访问的方法，然后一个类要是完全没有提供让外界访问的方法，那这个类没有意义了

继承的话，子类会继承父类的所有属性和方法，包括private修饰的，但是不能访问这些部分，子类可以拥有自己的属性和方法，==子类可以重写父类的方法==

多态的条件有三个，一：要有继承，二：子类需要重写父类的方法，三：父类引用指向子类实例

封装和继承让代码更复用，多态的话是让代码更容易移植，也更健壮

 ==多态：（一：要有继承/实现，二：重写方法，三：父类引用指向子类实例）==

​			==成员变量是不强调多态的==

## ==接口和抽象类有什么共同点和区别？==

共同点：

​	都不能直接实例化，接口需要被实现，抽象类需要被继承后才能创建具体的对象

​	都可以包含抽象方法，抽象方法没有方法体，必须在子类或实现类中实现



区别：

​	接口用于对类的行为进行约束，实现了某个接口就具有了对应的行为，==而抽象类是用于代码复用，强调所属关系==

​	一个类只能继承一个类（包含抽象类），但是可以实现多个接口,接口可以多继承接口

​	==接口中的成员变量只能用public static final修饰，不能修改且必须赋值，而====抽象类的成员变量可以有任何类型的修饰符，也可以在子类被重新定义和赋值==



## 深拷贝和浅拷贝了解吗？什么是引用拷贝？

深拷贝：完全复制整个对象，包括对象的内部对象

浅拷贝：会在堆上创建一个新的对象，如果原对象内部有引用类型，复制的是内部对象的内存地址，也就是说，拷贝对象和原对象共用同一个内部对象

引用拷贝：==两个不同的引用指向同一个对象==

![浅拷贝、深拷贝、引用拷贝示意图](https://oss.javaguide.cn/github/javaguide/java/basis/shallow&deep-copy.png)

## Object类的常见方法有哪些？

getClass()

hasCode()

equals()

clone()

toString()

notify()  唤醒一个线程

notifyAll() 唤醒所有线程

wait(超时时间)  暂停线程的执行

wait(超时时间，额外时间)

wait()

finalize(): 实例被垃圾回收器回收的时候触发的操作



## ==和equals()的区别

对于基本数据类型来说，==比较的是值

对于引用数据类型来说，==比较的是对象的内存地址是否相等

equals的话要分两种情况，一种是没有重写equals的，那它是等价于==，另一种是有重写equals的，比如String类，比较的是值是否相等



## hashCode()有什么作用？为什么要有hashCode？

获取哈希码，哈希码的作用是确定对象在哈希表中的索引位置，哈希表存储的是键值对，根据这个key可以快速找到所需要的对象，hashCode有以下特性，如果两个对象的hashCode不等，这两个对象不是同一个对象，如果两个对象的hashCode相等，两个对象不一定是同个对象，只有两个对象的hashCode相等并且equals方法也相等，才能说明它们是同个对象，所以hashCode还可以减少equals的次数，提高比较两个对象是否相等的效率。



## 为什么重写equals()方法还要重写hashCode()方法？

如果两个对象的hashCode相等，并不能说明两个对象的equals方法相等，因为可能是由于哈希碰撞，而两个对象的equals方法相等，可以说明两个对象的hashCode相等，如果只重写equals方法，可能会造成equals方法相等，但是hashCode又不相等。



## String,StringBuffer,StringBuilder的区别？

分三个方面：

1：可变性，String类型是不可变，而StringBuilder和StringBuffer都继承了AbstractStringBuilder,它们没有被private和final修饰，有修改字符串的方法，所以是可变的

2：线程安全：String中的对象不可变，可理解为常量，线程安全，StringBuffer有对方法或调用的方法执行同步锁，线程安全，StringBuilder没有对方法执行同步锁，线程不安全

3：性能：StringBuilder的性能比StringBuffer的性能好上10%-15%,但要冒线程不安全的风险

操作少量的数据：用String

单线程下操作大量数据StringBuilder

多线程下操作大量数据StringBuffer



## String为什么是不可变的？

两个原因：

1：保存字符串的数组被final修饰，并且没有提供修改字符串的方法

2：因为被final修饰，不能被子类继承，避免子类破坏String的不可变



## 字符串拼接用“+” 还是StringBuilder?

用StringBuilder好，因为+操作实际上也是调用StringBuilder的append方法再通过toString转成字符串的，并且在JDK9之前，使用+操作容易创建多个StringBuilder对象，JDK9之后，有一个动态方法可以去减少创建StringBuilder对象



## String的equals() 和 Object的equals()有何区别？

Object的equals（）比较的是两个对象的内存地址是否相等，等价于==，String的equals（）重写了Object的equals（），作用是比较两个字符串的值是否相等



## 字符串常量池的作用了解吗？

JVM特意开辟出来的节约内存，提高性能的一片区域，主要目的是为了避免字符串的重复创建



## String s1=new String("abc"),这句话创建了几个字符串对象？

可能创建一个或两个字符串对象

如果字符串常量池里面没有abc，会创建两个堆对象，其中一个放在字符串常量池，一个作为这个对象的引用

如果有找到，就只会创建一个堆对象，把这个堆对象的地址交给对象作为引用



String s2="abc"

它会先从字符串常量池去找这个对象的引用，如果没有才会在字符串常量池创建一个对象并返回引用，如果有直接返回那个引用



## String的intern方法有什么用？

==它是本地方法，作用是把字符串的引用保存到字符串常量池==

分两种情况

1.字符串常量池已经有这个对象的引用的话，它会直接返回引用

2.字符串常量池没有这个对象引用，会在常量池中建一个字符串的引用，然后再返回



## String类型的变量和常量做“+”运算时发生了什么？

在JavaC编译器中，有一个操作叫常量折叠，会影响到编译

final String str1 = "str";
final String str2 = "ing";
// 下面两个表达式其实是等价的
String c = "str" + "ing";// 常量池中的对象
String d = str1 + str2; // 常量池中的对象
System.out.println(c == d);// true



# Java基础（下）

## Excepetion和Error有什么区别？

首先，他们都有一个共同的父类Throwable,

Exception是程序本身可以处理的异常，用catch捕获，Exception分为checked exception（受检异常，必须处理的异常）和unchecked exception （不受检异常，程序可以不处理的异常）

Error是程序无法处理的错误，不建议用catch捕获，比如Java虚拟机运行时错误，虚拟机内存不够错误，类定义错误等异常发生后，Java虚拟机一般会选择线程终止



## Checked Exception和UnChecked Exception有什么区别？

Checked Exception是受检异常，程序必须处理的异常，==用catch捕获或throws 关键字抛出==，不然无法通过编译，除了RuntimeException及其子类外，其它异常都是受检异常，比如IO相关的异常，SQLException等

UnChecked Exception是不受检异常，程序可以不处理的异常，可以通过编译。RuntimeException及其子类就是不受检异常（运行时才出现的异常），常见的有空指针异常，非法参数异常



常见的有（建议记下来，日常开发中会经常用到）：

`NullPointerException`(空指针错误)

`IllegalArgumentException`(参数错误比如方法入参类型错误)

`NumberFormatException`（字符串转换为数字格式错误，`IllegalArgumentException`的子类）

`ArrayIndexOutOfBoundsException`（数组越界错误）

`ClassCastException`（类型转换错误）

`ArithmeticException`（算术错误）

`SecurityException` （安全错误比如权限不够）

`UnsupportedOperationException`(不支持的操作错误比如重复创建同一用户)



## Throwable类的常用方法是什么？

getMessage（）：打印异常信息的简要描述

toString(): 			   打印异常信息的详细信息

getLocalizeMessage(): 返回异常对象的本地化信息，==如果Throwable的子类没有重写这个方法，==他打印的和getMessage()方法一样

pringStackTrace(): 打印==Throwable对象==封装的异常信息



## try-catch-finally如何使用？

try:用于捕获异常，其后可以接0或多个catch，如果后面接0个catch，则必须使用finally

catch：用于处理捕获的异常

finally:无论是否捕获或处理异常，finally语句块都会执行，如果try或catch里面有return，则finally语句块会在方法返回之前执行。

注意不要在finally里面写return，如果try和finally里面都有return的话，try里面的return会被忽略  



## finally所在的代码块一定会被执行吗？

不一定，如果在执行finally之前==Java虚拟机终止==，finally代码块就不会被执行，或者==程序所在的线程死亡==，==关闭CPU==也会让代码块不被执行



## 如何用try-with-resource代替try-catch-finally?

try-with-resource是Java7出现的一种捕获异常的方式，和try-catch-finally类似，不过它比起try-catch-finally更简短，更清晰，产生的异常也更有利于我们，要使用try-with-resource的话要看两种情况：第一种情况是有实现closeable或AutoCloseable的对象，第二种情况是面对必须要关闭的资源或finally代码块执行的顺序，因为使用try-with-resource的话catch和finally代码块是在资源关闭后才执行的



## 异常使用有哪些需要注意的地方？

1：不要把异常定义成静态变量，因为这样会导致异常栈信息错乱

2：抛出的异常信息一定要有意义

3：抛出具体的异常，比如字符串转数字类型格式错误异常，你不要抛出非法参数异常

4：避免重复记录日志，在catch捕获的时候，已经记录的异常信息等，不要在业务抛出后，重复记录这个异常记录信息，这样不利于查找问题，也会让日志文件膨胀



## 什么是泛型？泛型有什么作用？

泛型是JDK5引入的一个特性，它可以在编译期间检查数据类型，减少强制类型转换以及可能出现的异常，使用泛型参数，提高了代码的可读性和稳定性

==本质：把具体的数据类型作为参数传给类型变量==

## 泛型方法的使用方式有哪几种？

泛型类，泛型接口，泛型方法



## 项目中哪里使用了泛型？

1：自定义接口结果返回类CommomResult<T>

2：Excel处理类ExcelUtils<T>可以动态处理excel导出的数据类型

3：集合工具类，比如Collections类的sort方法



不如浓缩成这个，谈谈你对泛型的理解

好的，泛型是jdk5引入的一个特性，==可以在编译期间检查数据类型，减少强制类型的转换以及可能出现的异常==，并且我们使用泛型参数，可以提高代码的可读性和稳定性，我们使用泛型的方法有三种，泛型类，泛型方法，泛型接口。然后我们经常可以在项目中看见到的泛型有：自定义通用结果返回类，ExcelUtils<>可以动态返回excel的数据格式，以及集合工具类Collections的sort排序方法，这些就是我对泛型的理解了。

## 什么是反射？

反射是框架的灵魂，反射赋予了我们在运行时分析类和执行类中方法的能力，它可以获取任意一个类的属性和方法，并且调用这些属性和方法



## 反射的优缺点？

优点：反射让我们的代码更加灵活，为框架开箱即用的功能提供了便利

缺点：==带来了安全问题==，它可以无视泛型参数安全检查，然后它的性能会稍差，不过对框架影响不大



## 反射的应用场景？

常见的地方是在框架，框架里面的动态代理也依赖反射，或者是注解



谈谈你对反射的理解？

反射是框架的灵魂，它赋予了我们在运行时分析类和执行类中方法的能力，它可以获取任意一个类的属性和方法，并且调用这些属性和方法

反射的优点，反射让我们的代码更加灵活，为框架开箱即用的功能提供了便利

缺点的话，带来了安全问题，它可以无视泛型安全参数的检查，并且性能稍差，不过对框架的影响不大

反射的应用场景主要是在框架，框架的动态代理依赖反射，或者注解



## 注解是什么？

注解是JDK5引入的一个新特性，注解本质上是一个继承了Annotation的特殊接口，它可以看成是一种特殊的注释，可以用来修饰类，方法，变量，==提供信息让程序在编译或运行时使用==。JDK内置了一些注解，如（@override，@Deprecated（标注该元素已被废弃））,我们也可以自定义注解



## 注解的解析方式有哪几种？

首先，注解只有被解析之后才能生效，有两种解析方法

1：编译期直接扫描：编译器扫描对应的注解并处理，比如@Override在编译期会检查方法是否有正确重写父类的方法，没正确重写就会有编译警告信息

2：运行期通过反射处理：很多框架基本都是通过反射处理，比如spring框架的@Value,@Component





谈谈你对注解的理解？

注解是jdk5引入的一个特性，它本质上是一个继承了Annotation的特殊接口，它可以看作是一种特殊的注释，可以用来修饰类，方法，变量，它提供了信息让程序在编译或运行时使用，JDK有一些内置的注解，比如@Orverride,@Resource等，我们也可以自定义注解

然后注解需要被解析之后才能生效

它有两种常见的解析方法，第一种是编译期间直接扫描：程序在扫描到对应的注解会进行处理，比如扫描到@Orverride的时候会注意程序是否有正确重写父类的方法，如果没有的话它会编译警告

第二种方法是运行时通过反射解析：很多框架也是在运行时通过反射解析的，比如Spring框架的@Component,@Value等





## 什么是SPI?

专门提供给服务提供者或有扩展框架能力的开发者去使用的接口，它可以把接口和具体实现分离开，把服务提供者和服务调用者解耦，提高程序的扩展性和可维护性，JAVA的一些框架有使用到了SPI机制，比如spring框架，dubbo的扩展机制

## API和SPI有什么区别？

首先，调用者调用接口，实现者实现接口，API主要是看实现者和接口，当调用者调用了接口，就具有了实现方提供好的功能。

SPI则主要看调用者和接口，调用者制定好规则，然后实现者根据规则去进行实现。

API有点像别人做了什么东西，我就用什么

SPI像我需要什么规则，别人根据规则去做



API是实现方提供好接口，调用者去调用接口，就可以使用实现方提前写好的功能

SPI是服务调用者制定了规范，实现方需要按照规范去执行，然后提供服务





## SPI有什么优缺点？

优点：SPI机制让接口设计更加灵活

缺点：需要遍历所有的实现类加载，不能按需加载，执行效率慢

​			多个ServiceLoader同时Load的时候，会有并发问题



谈谈你对SPI的了解？

SPI是专门提供给服务提供者或者有扩展框架能力的开发者去使用的一种接口，它将接口和具体实现分离开来。将接口提供者和接口调用者解耦，提高程序的扩展性和可维护性，Java的很多框架有使用到SPI，比如Spring框架，dubbo框架的扩展机制

它与API的区别的话，API是接口实现方实现了接口，调用方调用接口就能体验实现方提前写好的接口

SPI的话是接口调用方制定了规范，接口实现方按照规范实现接口

然后SPI机制让我们的接口设计更加灵活，

不够它只能同时加载所有的实现类，不能做到按需加载

然后多个ServiceLoader同时Load的时候，会有并发问题





## 什么是序列化？什么是反序列化？

序列化是将数据结构或对象转换成二进制字节流的过程

反序列化是将序列化过程中生成的二进制字节流转成数据结构或对象

序列化的主要目的是通过网络传输对象或是将对象存进文件系统，数据库，内存等。



像是JAVA中，序列化和反序列化都是用对象去做转换的

而在C++中，结构体对应的是数据结构，class对应的是对象类型

我们使用redis的话需要把对象序列化之后存进去，从redis中取出来需要把对象反序列化之后拿出来



## 序列化协议对应于TCP/IP 4层协议哪一层？

首先序列化协议是在OSI7层模型的表示层，然后表示层属于TCP/IP协议的应用层



## 如果有些字段不想序列化怎么办？

可以用transient关键字修饰，不过使用它的话有一些注意事项，

它只能修饰变量，不能修饰类和方法

==静态变量属于类，不属于实例，==无论有没有被transient关键字修饰，都不会被序列化

反序列化时，被它修饰的变量会恢复成类型的默认值，比如int会被恢复成0





## 常见序列化协议有什么？

有JDK自带的序列化方式，但是效率低且存在安全问题，一般不用，比较常用的Hession,kryo,protobuf,protostuff等基于二进制类型的协议

像JSON和XML这种文本序列化方法，可读性好，但是性能差一点，也不怎么选择



## 为什么不推荐使用JDK自带的序列化？

==1：不支持跨语言调用==

2：性能较差：相对于其它序列化协议，存储的字节数组较大，导致传输成本加大

3：存在安全问题：==反序列化的时候数据可以被用户控制，要是有人心怀不轨，就挺危险的==



了解序列化和反序列化吗？

序列化是把数据结构或对象转换成二进制字节

反序列化是把序列化中生成的二进制字节转换成数据结构或对象

序列化的主要目的是通过网络传输对象或把对象保存到文件系统或数据库，内存中

在Java中使用序列化的是对象，而像C++里面，结构体使用的是数据结构，类才是定义的对象

我们在项目中使用序列化的地方，把文件持久化，读文件需要反序列化，把对象存储进redis序列化，把序列化后的对象读出来需要反序列化

常见的序列化协议有JDK自带的序列化，不过它不支持跨语言调用，性能较差，存在安全问题，所以不使用，然后其它比较常用的序列化协议的话：Hession,Kryo,protobuf,protostuff等,然后像JSON和XML的序列化协议，虽然可读性好，性能稍差，也是不怎么常用

如果有字段不想通过序列化的话，可以用transient关键字，它的作用让字段不能通过序列化，并且反序列化之后的字段不能被持久化和恢复

序列化协议位于OSI七层模型的表示层，表示层是属于TCP/IP协议的应用层



## Java的IO流了解吗？

IO是input和output，把数据输入到计算机内存的过程叫输入，把数据输出到外部存储（像数据库，文件）这个过程叫输出。因为传输过程类似于水流，因此叫io流。==io流在Java中被分为输入流和输出流。根据数据处理方式不同分为字节流和字符流==

像InputStream和OutputStream分别是字节流的输入流和输出流

Reader和Writer分别是字符流的输入流和输出流



## IO流为什么要分为字节流和字符流？

字符流是Java虚拟机通过字节转换得到的，这个过程比较耗时

如果我们不知道编码类型，使用字节流很容易出现乱码问题



## 什么是语法糖？

语法糖是编程语言为了方便程序员开发程序而设计出来的一种特殊语法，不会影响到编程语言的功能，使用语法糖还能让程序看起来简洁且可读性更强。像增强for循环就是一个语法糖。然后在JVM中是不能识别语法糖的，需要通过编译器进行解糖操作，主要是靠Java编译器里面的compiler类的desugar()方法去负责这个解语法糖的实现



## Java中有哪些常见的语法糖？

有8种常见的语法糖，泛型，自动拆装箱，可变长参数，枚举，==内部类==，增强for循环，try-with-resource,lambda表达式



说说你对语法糖的了解？

语法糖是编程语言为了方便程序员开发程序而设计出来的一种特殊语法，不会影响到编译语言的功能。使用语法糖可以让我们的程序看起来简洁和可读性更强。然后JVM不能识别语法糖，需要通过java编译器去进行解糖操作后才能转换成JVM能识别的语法，主要是用到一个Compiler类的desugar()方法

常用的语法糖的话主要由8种，增强for循环，try-with-resource,lambda表达式，泛型，可变长参数，枚举，内部类，自动拆装箱

## Java中为什么只有值传递？

首先，值传递指的是实参传给方法后，形参如果在方法中改变值了，外界的实参是不会改变的，而引用传递则相反，形参如果在方法中改变值了，外界的实参是会跟着改变的。然后在Java中，

传一个基本类型，传递的其实是值的拷贝，方法内使用的是这个值的副本。对它进行操作并不会影响到实参，

而如果传一个引用类型，传递的是对象在堆内存中的地址值的拷贝，不过实参和形参是指向同一个具体数据对象的，然后Java为什么只有值传递，我看过一篇博客说可能是出于安全问题和简单问题考虑的。



# 学习Java基础之后的一些扩展

==是什么？可以做什么？==

==为什么？这个东西的好处？==

==怎么做？怎么使用？==





idea创建空项目



==基本类型的变量存的是数据，引用类型的变量存的是地址==

对象存储在堆内存单纯因为堆内存空间比较大，可以存



==工具类里面的构造方法私有就可以了，不要让使用者去通过创建对象的方式调用方法。直接让他类名.方法名就可以==



continue用于循环

break用于循环或者switch语句



快捷键

CTRL+ALT+L ：格式化代码

CTRL+SHIFT+ 箭头上下 ：移动代码 

==CTRL+ALT+T ：生成try -catch ,for循环之类==

CTRL+0（CTRL+SHIFT+空格，因为于输入法快捷键冲突，改成前面那个了） ：提示方法代码要输入什么

**导入模块**，先把文件夹放在电脑你哪里要打开的路径下，再去idea的最左上角的File里面的new右边的Module from Existing Sources ，选择好路径后选择那个黑点的文件（demo.iml）去导入,

![image-20240903113647530](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240903113647530.png)



![image-20240903113720604](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240903113720604.png)



## ==变量在计算机中的存储==

计算机用0，1这种二进制位去存储的,这种东西叫做位

然后计算机表示数据的最小存储单位1Byte（1字节）=8b（二进制位）



==字符在计算机中的存储方法==

有ASCII编码表，把数字对应的二进制码存到内存

'a':97  表示字符a

'A':65  表示字符A

'0': 48  表示字符0



==图片在计算机的存储方法==

把图片放大以后，不是有一个个像素点吗？每一个像素点都是三原色，像（255，255，255），这样就可以转换成二进制了，所以就是从左上角第一个像素点，一个一个把它们存进内存

==声音在计算机的存储方法==

声音是波形图，如果在每个坐标的纵坐标上面去取一些二进制数，再把它们存进内存

![image-20240903171716543](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240903171716543.png)

==视频的在计算机的存储方法==

一帧一帧的图片和声音去存



## ==自动类型转换：====(应该只有基本类型有)==

==小范围类型的变量可以赋值给大范围类型的变量,== 

==为什么要进行自动类型转换？==

==可能会需要不同类型的变量赋值给其它类型的变量==

==byte num1=-1;==

==int num2=num1;==

原理的话是看类型存储的字节，byte是1个字节，占8位，而int是4个字节，占32位，int可以装下8位的byte

![image-20240903202211824](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240903202211824.png)

==byte -> short -> int -> long ->float -> double==

​				==char ->int== 

![image-20240903202534672](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240903202534672.png)



## ==表达式的自动类型转换：==

运算结果通常与最大范围的变量类型一致，==但是byte，short,char类型在做表达式运算时，实际上转成int类型再去进行计算的==

常规情况

```
byte sa=20;
long sa2=100;
long l = sa + sa2;//120
```

特殊情况

```
char a='a'; //97
byte b=1;
short c=1;
int i = a + b + c;  //99
```

==为什么它们是转成int类型去计算呢？==

以byte类型举例（byte范围-128到127）

```
byte sa=120;
byte sa2=120;
int i1 = sa + sa2;
```

两者各种都是在byte范围内的，但是它们加起来就不一定还在byte范围内了，直接提到int范围避免错误



基本类型的强制类型转换

大范围的变量类型赋值给小范围的变量类型，（浮点数转成整数的话是丢掉自己的小数部分）

在小范围类型数据范围里面，正常结果不溢出

```
int b=10;
byte a= (byte) b;
System.out.println("int(b):"+b);  //10
```

不在小范围类型数据范围里面，结果溢出，导致结果为负数

```
int b=130;
byte a= (byte) b;
System.out.println("int(b):"+b);   //负数
```

这是怎么转的？

大的范围类型的变量，会去截取自己后多少位，放到小范围类型变量自己本身多少位里面，这时可能出现两种情况，

1：大范围数据在小范围类型数据范围里面，正常结果不溢出

2：大范围数据不在小范围类型数据范围里面，结果溢出，导致结果为负数



整数/整数，结果仍然是整数

```
int i=5;
int j=2;
System.out.println(i/j);  //2
```

要想转成浮点数：

```
double i=5.0;
int j=2;
System.out.println(i/j); //2.5
```

==或(下面这个挺有用的小技巧)==

```
int i=5;
int j=2;
System.out.println(1.0 * i / j); //2.5
```



==+号与字符串运算时会被当做连接符==（需要识别）

怎么识别呢？==从左到右能算则算，不能算当做连接符==

```
int a=20;
System.out.println(5+"a");  //5a 
System.out.println(a+"aa"); //20aa
System.out.println('a'+a);  //117，注意这里是单引号
```



自增自减不能操作字面量的，

不能2++；



赋值运算符，==隐含强制类型转换的==

```
byte a=10;
byte b=20;
a=a+b;  //注意这里编译报错，原因是运算时a是作为int，b也作为int，而用a+b赋值给a，这时a是不做运算的，是byte类型，所以编译报错
a= (byte) (a+b);//这样才是正确赋值
a += b         //它也等价于a= (byte) (a+b)
```



逻辑运算符

&  |  ！ ^

与 或 非 ==异或（左右条件结果相同为false，左右条件结果不同才为true）==

==&&  （这个的优先级比||的优先级高）==

短路与（左边条件错误就不执行右边条件了）

||

短路或（左边条件正确就不执行右边条件了）

优先级的示例

```
int i=10;
int j =45;
System.out.println(i<j || i<j && i==j); //因为&&的优先级高，先比较i<j && i==j，再比较i<j || 刚才的结果
```



if方法体中只有一行语句的话，可以省略{}

```

if(a>0) System.out.println(a);
```



==switch使用事项==

switch（表达式）  表达式中只支持是byte,short, int,char类型，枚举，String

case中不能是变量

break穿透，如果case中不写break；它会顺序执行下方语句，直到找到break；

(这个其实有时是可以简化代码的)

![image-20240904153300966](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240904153300966.png)



for循环 （==有索引的东西才能用for循环，比如List可以用，而Collection不能用==）

fori 可以快速生成for循环

求1-100之间的奇数，没想到的一种方法

```
int sum=0;
for (int i=1; i <= 100; i++) { //自己相的
    if(i%2==1)
    sum+=i;
}
System.out.println(sum);

sum=0;
for (int i = 1; i <=100 ; i+=2) {  //这样做是从1，3，5，7...去执行，还减少了for循环的判断次数
    sum+=i;
}
System.out.println(sum);
```



do-while :先执行后判断

应用场景：抢票，先执行再判断有没有抢到票，如果用while或for循环的话，都是先判断后执行，可能在判断的时候票就被抢走了



Random:

```
int i1 = random.nextInt(10); //0-9之间的数字
```

减加法，如果要生成3-17之间的随机数

（3-17） -3 ->  (0 - 14 ) +3

​	random.nextInt(15)+3

其实有生成指定范围的随机数的。但是JDK8没有这个课的那个方法，可能要JDK11或JDK17

random.nextInd(10,30);

但是应该也有,不过不找了





## 数组是什么？

容器，存储一批相同类型的数据，容器中的数据也叫做元素，是一种引用数据类型

静态初始化数组：定义的时候已经赋好值了

```
int[] age={16,26,36,6,100};
```

动态初始化数组

```
int[] arr=new int[5];
```

==注意两种定义类型不能混用，像以下是错误的==

```
int[] arr=new int[2]{1,2};//错误的写法
```

然后 int[]arr=new int[0]  等价于 int[] arr={};



int[]arr=null; ==代表arr这个变量在栈内存中的数据块中没有存放地址==

![image-20240905113400898](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240905113400898.png)



int[] arr={};==代表arr这个变量在栈内存中的数据块有存放地址，不过堆内存中的数据块是0个长度==

![image-20240905113640376](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240905113640376.png)



## ==数组在计算机中的存储，==

先为ages先开辟一块空间，然后等号右边又给它开辟一块空间，这块空间用地址表示，空间内有数据和索引。分配完右边的空间之后，左边空间就去存储右边空间的地址值并指向右边空间

![image-20240904174837853](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240904174837853.png)

动态化数组存进计算机的原理

和静态化类似，不过右边空间内的数据取的是类型的默认值

![image-20240904192935711](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240904192935711.png)

![image-20240904194940735](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240904194940735.png)



多个变量指向同一个数组

```
int[] arr1={1,2,3};
int[] arr2=arr1;

System.out.println(arr1);   //[I@61bbe9ba
System.out.println(arr2);	//[I@61bbe9ba
System.out.println(arr1 == arr2);  //true

arr2=null; //赋值为null之后，这个变量不再指向任何数组对象
System.out.println(arr2);//null

```

数组求最大值

我的思路

```
int[] arr={1,45,3,0,442,11};
int max=0;
int min=0;
for (int i = 0; i < arr.length; i++) {
    if(arr[i]>max){
        max=arr[i];
    }
    if(arr[i]<min){
        min=arr[i];
    }

}
System.out.println("max:"+max+"--min:"+min);
```

课上讲的思路

```
int[] arr={1,45,3,0,442,11};
int max=arr[0];
for (int i = 1; i < arr.length; i++) {
    if(arr[i]>max){
        max=arr[i];
    }

}
System.out.println(max);
```



数组反转

```
int[] arr={10,20,30,40,50};
int i1 = arr.length / 2;
int temp=0;
for (int i =0; i <arr.length; i++) {
    if(i==i1){
        break;
    }
    temp=arr[i];
    arr[i]=arr[arr.length-1-i];
    arr[arr.length-1-i]=temp;
}

for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}  //我的思路
```

```
int[] arr={10,20,30,40,50};

int temp=0;
for (int i =0,j=arr.length; i <j; i++,j--) {
    temp=arr[i];
    arr[i]=arr[arr.length-1-i];
    arr[arr.length-1-i]=temp;
}

for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}//课上的思路
```



随机排名 

让顺序随机

```
Random random=new Random();
Scanner sc=new Scanner(System.in);

int[] arr=new int[5];
for (int i = 0; i < arr.length; i++) {
    arr[i]=sc.nextInt();
    System.out.print(arr[i]+" ");
}
for (int i = 0; i < arr.length; i++) {
    int i1 = random.nextInt(5);
    int temp=arr[i];
    arr[i]=arr[i1];
    arr[i1]=temp;
}
System.out.println();
for (int i : arr) {
    System.out.print(i+" ");
}
```





## ==方法在计算机中的执行原理==

![](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240905104843934.png)



把数组按照特定输出内容打印//[11,22,33,44,55]

```
    int[] arr = {11, 22, 33, 44, 55};
    suchu(arr);


public static void suchu(int[] arr) {
    System.out.print("[");
    for (int i = 0; i < arr.length; i++) {
        System.out.print(i==arr.length-1? arr[i]:arr[i]+","); //注意这行代码，很优雅
    }
    System.out.println("]");

} //[11,22,33,44,55]
```



return在无返回值的方法中使用,直接结束方法

```
public void suchu(int[] arr) {
    if(arr==null){
        System.out.println("arr:"+arr);
        return;
    }
}
```



生成指定位数的验证码

我的代码

```
public static String modifyCode(int length){
    char[] arr2={
            'a','b','c','d','e','f','g', 'h','i','j',
            'k','l','m','n','o', 'p','q','r','s','t',
            'u','v','w', 'x','y','z',
            'A','B','C','D','E','F','G','H','I','J',
            'K','L','M','N','O','P','Q','R','S','T',
            'U','V','W','X','Y','Z',
            '0','1','2','3','4',
            '5','6','7','8','9'};

    Random random=new Random();
    String s="";
    for(int i=0;i<length;i++){
        //每一次生成一个随机数
        int suoyin = random.nextInt(62);
        s+=arr2[suoyin];
    }
    return s;
}
```

课上讲的

![image-20240905154853352](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240905154853352.png)



抽红包 , 这里每一次随机完后就把数据弄到要排序的第一位，然后下一次选择的随机数范围也跟着变

```
public static void hongbao() {
    int[] arr = {9, 666, 188, 520, 99999};

    Random random = new Random();
    Scanner sc = new Scanner(System.in);

    for (int i = 0; i < arr.length; i++) {
        System.out.print("请按任意键完成抽奖:");
        sc.nextLine();

        int i1 = random.nextInt(arr.length-i)+i;
        System.out.println("恭喜您抽到了:" + arr[i1]);
        int temp=arr[i];
        arr[i]=arr[i1];
        arr[i1]=temp;

    }
    System.out.println("活动结束");

}
```



## ==找素数==

```
public static int shusu2(){
    int count=0;
    for (int i = 101; i < 200; i++) {
        if(isShusu(i)){
            System.out.println(i);
            count++;
        }

    }
    return count;
}

private static boolean isShusu(int i) {

    for (int j = 2; j <= (i/2); j++) {
        if(i%j==0){
            return false;
        }
    }
    return true;

}
```

打印三角形

```
public static void sanjiao(){

    for (int i = 1; i<=5; i++) {
        //先打空格
        for (int j = 1; j <=5-i; j++) {
            System.out.print(" ");
        }

        //打*
        int count=0;
        for (int j = 1; j <=2*i-1 ; j++) {
            System.out.print(j%2==0?" ":"*");
            // System.out.print("*");

        }
        System.out.println();
    }

}
//输出
    *
   * *
  * * *
 * * * *
* * * * *
```



面向对象

## ==对象在计算机的执行原理==，[02、面向对象基础：对象执行原理，类与对象注意事项_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Cv411372m?p=70&spm_id_from=pageDriver&vd_source=f6ab15364078b5e23e959a13e65d9de4)

先在方法区引入Test.class，加载main方法到栈内存

栈内存中的方法扫描到Student时候，方法区加载Student.class,里面包含类的属性和方法

接着执行Student s1=new Student();

Student s1会在栈内存中开辟一块区域，等new Student()开始执行

new Student()执行过程，在堆内存中开辟一块区域，有

这块区域的地址

对象的属性，类实际地址==（并且类实际地址是指向方法区的Student.class的）==

new Student()执行结束之后，把地址填入栈内存中的s1，然后s1指向实际内存地址

变量赋值的话通过栈内存中的地址，修改堆内存中的属性的值

调用方法的话通过栈内存的地址，找到堆内存中存放的类实际地址，调用类实际地址里面的方法

![image-20240906102722100](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240906102722100.png)

如果没重写toString()方法的话，对象存的是地址，

com.xiaofan.data.Employee@61bbe9ba



堆内存的对象，如果没有被任何对象引用的话，会被自动内存管理回收GC，释放内存



this关键字：它是变量，用在方法中，拿到当前对象，主要是为了解决变量命名冲突的（比如构造方法中）

![image-20240906111900575](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240906111900575.png)

比如这个图，它在调用printThis之前把（类在堆内存开辟的变量的）地址交给this

编译器在编译会偷偷变成printThis(String this),去接这个地址



## ==String ,ArrayList  相关API讲解==

string的创建方式有两种,两种方式是等价的

```
//第一种：直接输入字符串
String s1="abc";

//第二种：new String()
String s2=new String();  //这里是创建了""(空字符串)
String s3=new String("abc");

char[] ch={'a','b','s'};
String s4=new String(ch);
System.out.println("s4:"+s4);//abs

byte[] by={97,65,48};
String s5=new String(by);
System.out.println("s5:"+s5);//aA0


```

String存的其实也是内存地址，但是底层做了处理，我们打印是直接打印内容了



## ==常用的StringApi==

![image-20240923201003533](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923201003533.png)

```
String test="sfas";
System.out.println("--------------");
//把字符串转成字符数组  {'s','f','a','s'}
System.out.println("原字符串:"+test);
System.out.print("转成字符数组后：{");
char[] chars = test.toCharArray(); 
for (int i = 0; i < chars.length; i++) {
    System.out.print( i!=chars.length-1? chars[i]+",":chars[i]);
}
System.out.println("}");
System.out.println("--------------");
//截取操作，和random.nextInt()一样，包前不包后的
System.out.println("原字符串:"+test);
String substring2 = test.substring(0, 2);
System.out.println("截取[0,2):"+substring2);

System.out.println("--------------");
//按照给定的东西进行前后分割后转成字符串数组，  如果没有分割成功，则字符串数组长度为1，一整个字符串作为一个数组
test="张无忌,张三丰,王五,啊啊";
String[] split = test.split(",");
for (int i = 0; i < split.length; i++) {
System.out.println(split[i]);
}
System.out.println(split.length);

```

==String的对象是不可变字符串对象，在计算机的执行原理中==

String name会在栈内存开辟一块空间存地址，

右边的"黑马"等价于new String("黑马"),在堆内存中开辟一块空间存，只要是以""写出的字符串，它是存在字符串常量池里面的。

然后把“黑马”的地址（119d7047）交给String name， String name再指向实际存放数据的黑马的地址

然后执行name += "程序员";

“程序员”先存放在字符串常量池，再进行“黑马”连接“程序员”变成“黑马程序员”（创建了一个新的堆内存对象）在（字符串常量池外面）

这个“黑马程序员”的地址自己会有一个地址(219ac47)，把这个地址再交给String name,覆盖掉刚才的地址



![image-20240906170639577](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240906170639577.png)



==结论：每次试图改变字符串对象，都会生成一个新的字符串对象，变量每次都是指向新的字符串对象，之前字符串对象的内容并没有改变。==



==用”“创建的字符串，会在堆内存的字符串常量池中创建==

==用new 方法创建的字符串，每new一次都会产生新的对象放在堆内存==

String s1=new String("abc"),这句话创建了几个字符串对象？

可能创建一个或两个字符串对象

如果字符串常量池里面没有abc，会创建两个堆对象，其中一个放在字符串常量池，一个作为这个对象的引用

如果有找到，就只会创建一个堆对象，把这个堆对象的地址交给对象作为引用



ArrayList：

无参默认创建的是10个容量，打印空集合,结果[]

```
ArrayList<String> list=new ArrayList<>();
list.add("aa");
list.add("bb");
list.add("cc");
list.add("bb");
list.add("dd");

//删除默认的第一个元素
list.remove("bb");
//根据索引删除
// list.remove(index);

list.set(1,"ee"); //修改指定位置的元素
System.out.println(list);

int size = list.size();
System.out.println("集合中元素的数量:"+size);
```



从集合中找出某些元素并删除（案例）

如果集合中包含枸杞就删除，（从前往后遍历（删除后需要让i--），因为是动态数组，删除一个后，后面元素往前移了，而i会继续往后走）

或者像下面从后往前遍历，就不会出现问题了

```
ArrayList<String> list=new ArrayList<>();
list.add("JAVA入门");
list.add("宁夏枸杞");
list.add("黑枸杞");
list.add("人字拖");
list.add("特级枸杞");
list.add("枸杞子");

for (int i = list.size()-1; i >=0 ; i--) {
	String s = list.get(i);
    if(s.contains("枸杞")){
    	list.remove(i);
    }
}
System.out.println(list);
```



## ==集合容器中存储的是对象的什么东西？对象的堆内存地址。==



## ==static关键字==

可以修饰变量和方法

==修饰变量的时候变量只会被分配一次内存==，==并且一般用public修饰,因为静态变量就是希望被别人共享，访问用的== 

```
public class StaticDemo1 {
    public static int num;

    public void print(){
        System.out.println(num); //在自己类中的静态变量可以省略类名
    }
}
```

静态变量（类变量）在计算机的执行原理

Student.name="袁华"；

扫描到Student，在方法区中加了Student.class,并且看见它（Student.class）里面有静态变量时，在堆内存中开辟了一块空间存“袁华”

![image-20240907192145406](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240907192145406.png)

静态方法在计算机中的执行

Student.printHelloWorld(); 扫描到Student.class的时候放到方法区

​												然后直接执行方法区里面的静态方法 printHelloWorld();



![image-20240907194013565](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240907194013565.png)

静态方法的应用场景：写在工具类里面的方法基本是静态方法，一个方法对应一个功能，

​							作用：代码复用，调用方便，工具类.方法名即可使用，提高开发效率



静态代码块

类加载的时候调用（通过类名.变量或类名.方法（）或new 对象的时候会调用，作用是为静态变量赋初始值）

普通代码块

new 对象的时候会调用（执行顺序在构造方法之前，作用为变量赋初始值）



## ==单例模式==

一个类只会被创建一次对象，单例模式的作用是避免浪费内存，比如任务管理器，运行时环境的Runtime类，只需要有一个就好了。

==饿汉式单例==：拿对象时，对象提前创建好了

用法：私有的构造方法，私有的静态变量创建一个对象，静态方法返回对象

private A(){}

==private static A a=new A();==

public static A getA(){

​	return a;

}

==懒汉式单例==：拿对象的时候再创建，以后用的时候再返回第一次创建这个对象

private A(){}

private static A a;

==public static A getInstance(){==

​	==if(a==null){==

​		==a=new A();==

​	==}==

​	==return a;==

==}==

==枚举实现单例==

```
public enum B {
    X;
}
```



==继承下的类在计算机中的执行原理==

B b=new B();

B b在栈内存创建一个对象，new B在堆内存开辟了空间，然后注意了，空间里面的数据是B和父类A共有的所有的属性，b指向new B开辟出来空间的地址

![image-20240907210158184](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240907210158184.png)



==Java中的类都是直接或间接继承了Object类的==



方法重写主要是用于重写Object类的toString()方法，平时我们打印一个对象默认就是调用的toString()方法

```
ATM atm=new ATM();
System.out.println(atm);
System.out.println(atm.toString());
```



==子类的构造器执行之前都会先执行父类的构造器方法,因为会默认执行super()====,可以自己进行手动覆盖的==

public zi(){

​	super();//不用手写也会默认生成

​	sout("aa");

}

public zi(String name){

​	super();//不用手写也会默认生成

​	sout(name);

}

子类构造器调用父类构造器

![image-20240908020536598](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240908020536598.png)



this()调用同个类中的其它方法重载的构造器 ，==类的构造器方法中不能既写this(),又写super()==

![image-20240908020932387](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240908020932387.png)

 ==多态：（一：要有继承/实现，二：重写方法，三：父类引用指向子类实例）==

==成员变量是不强调多态的==,（编译看左边，执行也是看左边）

```
public class Test {
    public static void main(String[] args) {
        People stu=new Student();
        System.out.println(stu.name); //people
        stu=new Teacher();
        System.out.println(stu.name); //people

    }
}

class People{
    public String name="people";
}
class Student extends People{
    public String name="student";
}
class Teacher extends People{
    public String name="teacher";
}
```



## ==多态==

使用多态好处：解耦合，在方法的形参中放父类参数，调用这个方法可以使用子类参数

​				问题：多态下子类没法调用它自己的独有的方法（编译的时候检查父类有的方法，父类没有这个独有的方法，报错）



自动类型转换  

强制类型转换(解决子类不能调用它自己的独有的方法)

```
People stu=new Student(); //自动类型转换  
if(stu instanceof Student){  //如果stu是Student类或者Student子类，可以强转
    Student s1= (Student) stu;//强制类型转换
    s1.test();
}
```



## final关键字：可以修饰类，方法变量，

修饰类：类不能被继承

修饰方法：方法不能被重写

修饰变量：变量只能被赋值一次



常量：被static final修饰的成员变量，所有单词字母大写，多个单词之间用_连接

可读性好，可维护性好，被编译时会进行宏替换操作，跟使用字面值（类似123,"aaa"）一样，性能好



==抽象类：被abstract修饰的类，==

抽象类可以没有抽象方法， 但是有抽象方法的类一定是抽象类

普通类该有的（成员变量，属性，方法）抽象类都可以有

抽象类不能直接实例化，必须由其子类实现

作为一个特殊的父类让子类继承， ==子类一旦继承抽象类，必须重写所有的抽象方法或者子类也作为一个抽象类==

抽象方法：被abstract修饰的方法



抽象类的场景和好处

因为子类重写抽象类必须实现所有的抽象方法（自己作为抽象类的可能性不提），让子类自己去实现方法，父类引用到时可以使用子类的方法

A a=new B(); //假设A是抽象类

a.run(); //父类有这个方法，编译可以通过，但是具体调用的是子类的实现行为

主要是为了支持多态，



模板方法设计模式

==解决了方法中存在重复代码的问题==

用法：定义一个抽象类，抽象类中写一个final 修饰的方法（里面写重复的代码，在需要子类自己实现的时候调用抽象方法）,再写一个抽象方法，具体交给子类去实现。

![image-20240908144937018](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240908144937018.png)

```
public class Test2 {
    public static void main(String[] args) {
        A b=new B();
        b.say(); // hha
                    写了B改写的东西
                    结束拉
        A c=new C();
        c.say();  //hha
                    写了C改写的东西
                    结束拉
    }
}
abstract class A{

    public final void say(){
        System.out.println("hha");
        write();
        System.out.println("结束拉");
    }

    public abstract void write();
}
class B extends A{


    @Override
    public void write() {
        System.out.println("写了B改写的东西");
    }
}
class C extends A{


    @Override
    public void write() {
        System.out.println("写了C改写的东西");
    }
}
```



接口：被interface修饰的类，接口中只能有常量和抽象方法

类可以多实现接口，实现接口需要把接口中的抽象方法都实现，不然自己要变成抽象类

使用接口好处：1：解决单继承问题，可以扩展类的功能 2：面向接口编程，灵活切换业务逻辑



==JDK8开始接口新增的三种方法：==

默认方法

私有方法

静态方法 

主要是为了增强接口的功能，便于项目的扩展和维护



匿名内部类:==在编译的时候把new的对象当成子类（或者接口的实现类），再去创建子类（或者接口的实现类）的对象；==

new 类/接口（）{

​	@Override

​	void print(){

}

}

使用场景：作为参数传给方法

![image-20240909225303849](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909225303849.png)

枚举

![image-20240909231613092](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909231613092.png)

![image-20240909231524687](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909231524687.png)



抽象枚举

![image-20240909231441895](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909231441895.png)



使用枚举可以写单例

```
public enum B {
    X;
}
```



==枚举的作用（类似常量，但是常量作为参数传给方法时还可以往里面传字面值，整数之类）==

==做信息标志和分类==

枚举和常量并不是互相淘汰的，常量用起来简单，两种都可以用

![image-20240910100019276](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910100019276.png)



```
throw new BusinessException(ErrorCode.SYSTEM_ERROR, "上传失败");
```

## ==泛型类==

下面的这个MyArrayList<E>里面

首先不确定要放的有什么类型的数据，所以用Object数组，默认初始容量10，封装的思想用private

再用一个size定义当前位置 ，基本类型成员变量的默认值是类型的默认值，size=0

add(E e)方法的时候arr[size++] = e   实际上是做了arr[size]=e  ,size++;

get(int index)的时候，返回值先帮我s们强转了，我们就不用在使用的时候自己强转了

![image-20240910102207689](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910102207689.png)

多个泛型参数的时候

![image-20240910102815937](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910102815937.png)

限定泛型参数必须是某个类或者是它的子类

![image-20240910103040628](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910103040628.png)

## ==泛型接口==

![image-20240910103724084](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910103724084.png)

注意接口里面的泛型参数也是可以继承某一个类的

![image-20240910103829899](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910103829899.png)



## ==泛型方法==

注意第三个不是泛型方法，因为它里面的返回值E是通过MyArrayList<E>这个泛型类的参数得到的

![image-20240910104113148](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910104113148.png)

![image-20240910104212181](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910104212181.png)

泛型方法的两种常见方式

```
public static <T extends Car> void compete(ArrayList<T> t){

}


//？指  在  “使用 ” 泛型的时候可以定义一切类型   
？ extends Car(上线)
？ super Car (下线) 类型必须是Car或者是Car的父类
 public static void compete(ArrayList<? extends Car> t){

 }
 

```

泛型擦除   编译阶段的<String>，在编译成.class后会被去掉

![image-20240910110412048](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910110412048.png)



==泛型不支持基本类型，只支持引用类型==





重写equals方法的讲解

Objects.equals()  这个比String类的equals方法多做一层判空处理

```
String a=null;
String b="itheima";
System.out.println(Objects.equals(a,b));	//false
System.out.println(a.equals(b));          //空指针异常
```

![image-20240910155702331](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910155702331.png)



## ==常用API==

对象克隆要implements Cloneable，然后要重写

```
public class Student implements Cloneable{

    @Override
    protected Object clone() throws CloneNotSupportedException {
        Student clone = (Student) super.clone();
        clone.arr = clone.getArr().clone();
        
        return clone;
    }
```



Objects工具类

equals() ：先做判空处理，再比较

```
String a=null;
String b="itheima";
System.out.println(Objects.equals(a,b));  //false
System.out.println(a.equals(b));		  //空指针异常
```

isNull():判断是否为空

Objects.isNull(s1)  内部其实就是执行判断 s1==null

![image-20240910164950735](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910164950735.png)



Objects.nonNull()：判断不为空



基本类型（包装类型也可以）与字符串之间的转换

```
int i1=14; 
String s = Integer.toString(i1);  //把基本类型转成字符串   不如直接+"" 也是变成字符串
System.out.println(s+1);   //141

int aa=Integer.valueOf(s); //把字符串转成基本类型
System.out.println(aa+1);  //15
```



StringBuilder,StringBuffer,StringJoiner

StringBuilder:可变字符串对象，相当于是一个容器，可以用来操作字符串，支持链式编程

常用方法

![image-20240910172659710](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910172659710.png)

==如果字符串频繁的拼接修改，用StringBuilder效率高很多==



==StringBuffer与StringBuilder用法一样，只不过StringBuffer线程安全，StringBuilder线程不安全==



StringJoiner  和StringBuilder一样，但是语法可能更简洁

![image-20240910180347091](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910180347091.png)



Math工具类

![image-20240911110132562](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911110132562.png)



System工具类

![image-20240911111724519](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911111724519.png)

```
// System.out.println("aa");
// System.exit(0); // 终止Java虚拟机 非0代表异常退出 ，以下程序都不执行
//实际上是调用Runtime.getRuntime().exit(status);，得到Runtime对象，调用退出方法

// System.out.println("cc");

long start = System.currentTimeMillis();//系统的当前时间 毫秒值，要得到秒的话要➗1000
System.out.println("开始时间："+start/1000);
for (int i = 0; i < 100000; i++) {
    System.out.println("i");
}

long end = System.currentTimeMillis();
System.out.println("结束时间："+end/1000);

System.out.println("总共经历了:"+(end-start)/1000+"秒");
System.out.println("总共经历了:"+(end-start)/1000.0+"秒"); // ➗1000.0主要是得到小数位
```



Runtime类的API

![image-20240911112954190](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911112954190.png)



Bigdecimal

==用String类型的参数入参，或者静态方法的valueOf  把double转成Bigdecimal,才能正确解决精度丢失==

==因为用double存取的，最后还要用doubleValue把它转成double类型==

![image-20240911140939980](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911140939980.png)



Date

```
Date date=new Date();
System.out.println(date);  //Wed Sep 11 14:28:46 CST 2024
```

![image-20240911142449481](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911142449481.png)

==SimpleDateFormat : 简单日期格式化==  ，

把奇怪的日期格式转成用户看得懂表示： 

```
("yyyy年MM月dd日 HH:mm:ss EEE a")
```

 Wed Sep 11 14:47:44 CST 2024   -->   2024年09月11日 14:47:44 星期三 下午   

![image-20240911145108145](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911145108145.png)

![image-20240911143625287](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911143625287.png)

把字符串转成日期

![image-20240911145255311](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911145255311.png)



日历 

![image-20240911153103958](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911153103958.png)



为什么要学JDK1.8

简单来说，就是设计的不合理呗

![image-20240912191046470](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912191046470.png)

![image-20240912191028815](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912191028815.png)



LocalDate

parse方法把字符串解析成LocalDate

![image-20240920201652462](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240920201652462.png)

![image-20240912192355306](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912192355306.png)

![image-20240912192335684](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912192335684.png)



LocalTime

![image-20240912194450041](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912194450041.png)



LocalDateTime:除了静态方法of可以传LocalDate,LocalTime转成LocalDateTime之外，其它跟上面两个方法一样

```
LocalDate localDate=LocalDate.now();
LocalTime localTime=LocalTime.now();
LocalDateTime of = LocalDateTime.of(localDate, localTime);
```



时区相关的（有用到的时候再去看吧，基本没见过这方面需求）

![image-20240912200506624](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912200506624.png)





Instant:用来替代Date的

now方法得到对象，可精确到纳秒级

做代码的性能分析，或者记录用户的操作时间的（比如记录一下什么时候执行这个操作的）

![image-20240912201536273](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912201536273.png)



DateTimeFormatter(代替SimpleDateFormat)

![image-20240912205008309](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912205008309.png)



## 做倒计时相关业务用的

Period:一段时间（计算时间间隔，年，月，日）



between方法的两个参数只能放（前后），不然会出错的

![image-20240912211629680](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912211629680.png)

Duration:一段时期（感觉就是计算时，分，秒）

![image-20240912212031358](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912212031358.png)



## Arrays工具类

```
String[] arr={"aa","bb","cc"};
String s = Arrays.toString(arr);  //把数组转成字符串
System.out.println(s);
[aa, bb, cc]

//注意这个copyOf方法，它是复制数组，并扩容长度，长度>原数组的话，剩下的元素补默认值，比如String类型补null，int类型补0
String[] strings = Arrays.copyOf(arr, 10); 
[aa, bb, cc, null, null, null, null, null, null, null]

长度<原数组的话，缩容
String[] strings = Arrays.copyOf(arr, 2);
[aa, bb]
```

![image-20240912214321289](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912214321289.png)

感觉就一个toString实用一点。



sort也能稍微讲一下，如果是对一个对象排序，需要自定义排序，有两种方法。

![image-20240912215446130](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912215446130.png)

![image-20240912220045368](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912220045368.png)

![image-20240912220021992](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912220021992.png)



## 正则表达式：1：校验

![image-20240921151417418](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240921151417418.png)

![image-20240921152117329](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240921152117329.png)

[] :匹配单个字符

.  匹配单个字符

\d :0-9 (单个字符)

\s :代表空格

\w  [a-zA-Z_0-9]

\W  不能是[a-zA-Z_0-9]



？ 0个或1个

*：至少0次

+：至少1次

{n}:正好n次

{n,}:至少n次

{n,m} : n到m次 [n,m]

(?i): 忽略大小写字母

|  或



正则表达式第二个功能，爬取信息

![image-20240921163633693](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240921163633693.png)

![image-20240921164839065](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240921164839065.png)



## 异常

RuntimeException是运行时异常，比如数组索引越界异常，

为什么要有这种异常呢？

程序员水平不行出现的异常，所以都不想提醒你



![image-20240921170009862](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240921170009862.png)

自定义异常

![image-20240921171516298](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240921171516298.png)

开发中处理异常

![image-20240921173215316](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240921173215316.png)

这种写法背那个八股文的时候，说很好。然后黑马视频说实际开发的时候直接抛出Exception就好了，方便处理

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240921173711417.png" alt="image-20240921173711417" style="zoom: 67%;" />

![image-20240921173855479](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240921173855479.png)

==下面这个图可以看一下的，捕获异常后尝试修复==

![image-20240921174241266](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240921174241266.png)



## 集合

Collection集合：存储单一元素，（集合中存储的是元素的地址）

![image-20240922185651870](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922185651870.png)



Collection的常用方法

![image-20240922191333950](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922191333950.png)

遍历集合的三种方式：

迭代器，

![image-20240922192906005](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922192906005.png)

增强for循环

![image-20240922193049360](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922193049360.png)

lambda表达式遍历map集合的时候才能感受到方便

![image-20240922193722116](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922193722116.png)

```
c1.forEach(new Consumer<String>() {
    @Override
    public void accept(String s) {
        System.out.println(s);
    }
});
c1.forEach(s-> System.out.println(s));
c1.forEach(System.out::println);
```

![image-20240922194256917](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922194256917.png)



## List集合

==还有一个addAll方法，同种集合追加元素==

```
List<String> s1=new ArrayList<>();
s1.add("11");
s1.add("aa");
List<String> s2=new ArrayList<>();
s2.add("asd");
s1.addAll(s2);
System.out.println(s1);  //[11, aa, asd]
```

==subList（）：从哪个索引开始，包前不包后==

```
cards.subList(cards.size()-3,cards.size());
```

![image-20240922195057355](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922195057355.png)



### ArrayList(底层原理):

![image-20240922200125817](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922200125817.png)

### ListedList(底层原理)：

双向链表，Java在大多数情况下都会采用双向链表，（==对首尾元素进行增删改查的速度极快==）

![image-20240922203059656](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922203059656.png)

双向链表相对于单向链表来说的话，查询会更快一点，因为它可以判断索引是离头节点近一点，还是离尾节点近一点

![image-20240922203132447](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922203132447.png)



==它（LinkedList）自己有独有的方法（因为它的头尾操作速度极快），==

==应用场景：队列，栈（push入栈,pop出栈）==

```
LinkedList<String> queue=new LinkedList<>();//不用List声明是因为父类中不能使用子类特有的方法，（编译时没有）
        queue.addLast("第一号");
        queue.addLast("第二号");
        queue.addLast("第三号");
        queue.addLast("第四号");

        System.out.println(queue);

        System.out.println(queue.removeFirst());
        System.out.println(queue.removeFirst());
        System.out.println(queue.removeFirst());
        System.out.println(queue.removeFirst());
```



## Set集合

TreeSet(升序排序)

![image-20240922205934641](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922205934641.png)

HashSet 无序：==不代表每次打印出来的东西是随机的==，它只是说元素在集合中的存储不是按照索引方式，而是按照元素的哈希值，定下来以后下次打印仍然是以前的模样。

```
Set<Integer> set=new HashSet<>();
set.add(666);
set.add(666);
set.add(999);
set.add(69);
set.add(999);
System.out.println(set);//[69, 999, 666]
```

比如上面第一次定下来是[69, 999, 666]了，往后几次打印还是[69, 999, 666]



LinkedHashSet是有序，不可重复，无索引



### HashSet(底层原理)

基于哈希表实现

==哈希表是一种增删改查，性能都较好的数据结构（综合）==

![image-20240922211139460](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922211139460.png)

![image-20240922211653806](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922211653806.png)

jdk8之后

![image-20240922212756310](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922212756310.png)

红黑树怎么找到元素的大小？

小的哈希值往左边，大的哈希值往右边

(Integer1的hashCode是1，Integer50的hashCode是50)



二叉树（了解一些基本概念即可，开发无实际意义）

![image-20240922213052080](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922213052080.png)

二叉排序树（二叉查找树）

![image-20240922213657383](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922213657383.png)

二叉查找树存在一些问题

![image-20240922213642664](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922213642664.png)

平衡二叉树

![image-20240922213806250](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922213806250.png)



红黑树：有算法维护让它自平衡，树的分布均衡

![image-20240922213847202](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922213847202.png)

![image-20240922214956209](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240922214956209.png)



### LinkedHashSet(底层原理)

第一个元素的情况，哈希值对数组长度求余后就插入位置，然后需要头针和尾针记录

![image-20240923092102070](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923092102070.png)



![image-20240923092024788](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923092024788.png)

第二个元素的话

==1： 先找到尾针==

==2：把第二个元素的地址送给前一个元素，让前一个元素指向第二个元素==

==3：它也会拿前一个元素的地址，让自己指向它==

==3：修改尾针到第二个元素==

![image-20240923092449576](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923092449576.png)

==因为每个元素都额外多了双链表记录它前后元素的位置，所以消耗内存==

### TreeSet

![image-20240923093931806](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923093931806.png)

![image-20240923093643203](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923093643203.png)

![image-20240923093821786](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923093821786.png)

## 并发修改问题

“并发”是指多个线程或任务同时执行的能力。这种能力使得程序能够在同一时间处理多个任务，从而提高效率和响应速度。

![image-20240923095506869](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923095506869.png)

## 可变参数

![image-20240923101047413](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923101047413.png)



## Collections工具类

![image-20240923101830252](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923101830252.png)



## Map

![image-20240923141806232](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923141806232.png)

==map的不重复指的是key的不重复，后声明的会覆盖先声明的==

还有一个追加Map集合的方法叫putAll(),和list的那个addAll()方法一样

```
Map<String,Integer> map1=new HashMap<>();
map1.put("java1",10);
map1.put("java2",20);
Map<String,Integer> map2=new HashMap<>();
map2.put("java",222);
map2.put("java2",222);
map1.putAll(map2);
System.out.println(map1);
//{java2=222, java=222, java1=10}
```

![image-20240923144425523](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923144425523.png)



map的遍历方式

1：

![image-20240923151003669](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923151003669.png)

2：

![image-20240923150926499](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923150926499.png)

这种entrySet的方式不太常用

3：==lambda表达式（推荐使用）==

![image-20240923152423888](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923152423888.png)

### HashMap:

![image-20240923154741353](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923154741353.png)

### LinkedHashMap:

有序（仍然是那个添加的顺序和取出的顺序是一致的），不可重复，无索引

![image-20240923155834497](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923155834497.png)

### TreeMap:

![image-20240923160032113](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923160032113.png)

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



## File（操作文件用的）,IO流

==file类的对象可以是文件或文件夹==

![image-20240923175048750](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923175048750.png)

如果需要读写数据，就用到了IO流（可以读写文件或网络中的数据）

![image-20240923175236555](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923175236555.png)

![image-20240923180016626](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923180016626.png)

![image-20240923190904730](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923190904730.png)

![image-20240923191328775](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923191328775.png)

```
File file = new File("java8-lambda-and-stream/src/main/java/com/xiaofan/aa.txt");
```

![image-20240923192425383](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923192425383.png)

![image-20240923193752788](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923193752788.png)

![image-20240923194306389](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923194306389.png)



## 方法递归

![image-20240923201702762](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923201702762.png)

==猴子摘桃的递归解决==

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240923205504224.png" alt="image-20240923205504224" style="zoom: 80%;" />



业务里面，递归不一定有公式的。

==遍历文件夹搜索文件==

```
public static void searchFile(File dir,String fileName){
    //先判断传入的参数 是否为null，是否存在，是否是文件
    if(dir==null || !dir.exists() || dir.isFile()){
        return;
    }

//    可以确定现在传入的是一个目录了，需要遍历这个目录的一级文件夹去找
    File[] files = dir.listFiles();
    for (File f : files) {
        //如果一级文件夹中是文件
        if(f.isFile()){
            //判断文件名字是否是要查找的名字
            if(f.getName().equals(fileName)){
                System.out.println(f.getAbsolutePath());
            }
        }//一级文件夹中不是文件
        else{
            searchFile(f,fileName);
        }
    }
}
```



## 字符集

![image-20240924135141781](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924135141781.png)

Unicode：万国码，国际组织搞出来的东西

![image-20240924135740914](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924135740914.png)



字符集的编码，解码

编码：把字符按照指定字符集编码成字节

解码：将字节按照指定字符集解码成字符

![image-20240924140527338](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924140527338.png)

![image-20240924141204767](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924141204767.png)



## IO流

![image-20240924142021363](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924142021363.png)

![image-20240924142231617](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924142231617.png)

![image-20240924142446504](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924142446504.png)



### FileInputStream

![image-20240924142810437](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924142810437.png)

![image-20240924143014718](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924143014718.png)

![image-20240924144101530](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924144101530.png)

![image-20240924151827129](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924151827129.png)

### FileOutputStream

![image-20240924153350737](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924153350737.png)

```
OutputStream outputStream=new FileOutputStream("java8-lambda-and-stream\\src\\main\\java\\com\\xiaofan\\bb.txt",true);

byte[] bytes = "我爱你中国abc".getBytes();
outputStream.write("\r\n".getBytes());
outputStream.write(bytes,0,12);

outputStream.close();
```



![image-20240924154820960](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924154820960.png)

复制文件

```
//文件复制
File file=new File("F:\\temp.jpg");
InputStream inputStream=new FileInputStream(file);
OutputStream outputStream=new FileOutputStream("F:\\temp1.jpg");

byte[] bytes = new byte[1024];
//把内容读取到bytes数组中了
int length;
while((length=inputStream.read(bytes))!=-1){
    outputStream.write(bytes,0,length);
}

outputStream.close();
inputStream.close();
```

### 释放资源

try-with-resource

```
//文件复制
try (
        InputStream inputStream = new FileInputStream("F:\\temp.jpg");
        OutputStream outputStream = new FileOutputStream("F:\\temp1.jpg");
) {
    byte[] bytes = new byte[1024];
    //把内容读取到bytes数组中了
    int length;
    while ((length = inputStream.read(bytes)) != -1) {
        outputStream.write(bytes, 0, length);
    }

} catch (IOException e) {
    e.printStackTrace();
}
```

![image-20240924160801313](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924160801313.png)



### FileReader

![image-20240924162726247](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924162726247.png)



### FileWriter

![image-20240924162706903](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924162706903.png)

![image-20240924163450383](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924163450383.png)



## 缓冲流

![image-20240924171711465](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924171711465.png)

### 字节缓冲流

![image-20240924171959875](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924171959875.png)



![image-20240924172307547](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924172307547.png)



### 字符缓冲流

#### BufferedReader

![image-20240924172602640](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924172602640.png)

![image-20240924172626358](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924172626358.png)

![image-20240924172844209](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924172844209.png)



#### BufferedWriter

![image-20240924173007305](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924173007305.png)

![image-20240924173034305](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924173034305.png)



### 关于性能问题：

==不一定说低级流的就慢过缓冲流，低级流可以通过设置数组的大小，这个设置不是越大越好的，它是里面有顶点的，再大其实意义不大了,达到和缓冲流差不多的程度，不过建议还是使用缓冲流（它里面有8GB默认缓存）==

![image-20240924180453794](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924180453794.png)

### 转换流

![image-20240924185620217](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924185620217.png)

![image-20240924185702970](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924185702970.png)



#### 字符输入转换流

![image-20240924185802722](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924185802722.png)

![image-20240924190155791](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924190155791.png)字符输出转换流

![image-20240924190415346](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924190415346.png)

### 打印流



![image-20240924191357162](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924191357162.png)

![image-20240924192609723](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924192609723.png)

![image-20240924192910342](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924192910342.png)



数据流

#### 数据输出流

![image-20240924194720821](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924194720821.png)

数据输入流

![image-20240924194951481](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924194951481.png)



序列化流

![image-20240924195315554](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924195315554.png)



要序列化的类必须要实现Serializable

![image-20240924195640754](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924195640754.png)

![image-20240924195758720](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924195758720.png)



反序列化作用：ObjectInputStream

![image-20240924195843516](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924195843516.png)

![image-20240924200003463](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924200003463.png)

transient关键字修饰变量可以让对象的属性不被序列化

![image-20240924200217784](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924200217784.png)



## IO框架（底层还会优化性能）

![image-20240924203844971](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240924203844971.png)

## 特殊文件（properties,xml）

![image-20240925105921082](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925105921082.png)

![image-20240925105954826](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925105954826.png)

![image-20240925110154989](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925110154989.png)

解析xml

![image-20240925110455330](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925110455330.png)

![image-20240925111106797](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925111106797.png)

![image-20240925111212308](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925111212308.png)

约束文档

![image-20240925111500711](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925111500711.png)

![image-20240925111511284](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925111511284.png)

![image-20240925111540318](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925111540318.png)



## ==日志：==

![image-20240925111839477](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925111839477.png)

![image-20240925112012666](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925112012666.png)

![image-20240925112236514](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925112236514.png)

![image-20240925112429298](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925112429298.png)

```
//slf4j包下
public static final Logger LOGGER=LoggerFactory.getLogger("IOtest");
LOGGER.info("aa");
LOGGER.error("危险");
LOGGER.debug("debug");
```

核心配置文件（==调整日志输出格式==   11:34:24.693 [main] INFO IOtest - aa

，==输出的文件放在哪个目录==，开关日志，日志文件到达某一个大小后会压缩，然后继续存

==日志级别==

）

![image-20240925113731121](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925113731121.png)

![image-20240925114319345](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925114319345.png)

![image-20240925115054025](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925115054025.png)



## ==多线程==

线程：程序内部的一条执行流程

![image-20240925115531216](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925115531216.png)



多线程（可以同时做多件事情）

![image-20240925115945569](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925115945569.png)

比如

网盘：可以一边下载，一边上传，两条执行流程

12306：很多用户的购票请求

消息通信：一边发消息，一边收消息





### 创建线程的方式

#### 1:继承Thread

![image-20240925121104980](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925121104980.png)

```
public class ThreadTest1 {
    public static void main(String[] args) {
        //创建MyThread线程类的对象代表一个线程  创建线程
        Thread t=new MyThread();
        //启动线程(自动执行run方法)
        t.start();
        for (int i = 0; i <= 5; i++) {
            System.out.println("主线程main输出："+i);
        }

    }
}

class MyThread extends Thread{

    @Override
    public void run() {
        for (int i = 0; i <= 5; i++) {
            System.out.println("子线程MyThread线程输出："+i);
        }
    }
}
```



#### 2:实现Runnable接口

![image-20240925122350019](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925122350019.png)

```
Runnable r=new MyRunnable();
new Thread(r).start();

for (int i = 0; i <= 5; i++) {
    System.out.println("主线程main输出：" + i);
}

class MyRunnable implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i <= 5; i++) {
            System.out.println("子线程MyRunnable线程输出：" + i);
        }
    }
}
```



#### ==3：实现Callable（能够得到返回值）==

![image-20240925122929738](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925122929738.png)

![image-20240925125200403](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925125200403.png)



```
Callable c = new MyCallable(100);
        FutureTask<String> f1 = new FutureTask<>(c);
        new Thread(f1).start();
        System.out.println(f1.get());
        

class MyCallable implements Callable<String> {
    private int n;

    public MyCallable(int n) {
        this.n = n;
    }

    /**
     * Computes a result, or throws an exception if unable to do so.
     *
     * @return computed result
     * @throws Exception if unable to compute a result
     */
    @Override
    public String call() throws Exception {
        int sum = 0;
        for (int i = 0; i <= n; i++) {
           sum+=i;
        }
        return "线程执行完毕,求出了1-"+n+"的和是："+sum;
    }
}
```

![image-20240925125320213](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925125320213.png)

常用方法

![image-20240925140703713](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925140703713.png)

![image-20240925141946146](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925141946146.png)

![image-20240925142018329](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925142018329.png)

### ==线程安全==

多个线程，同时操作同一个共享资源的时候，可能会出现业务安全问题



![image-20240925142844237](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925142844237.png)

![image-20240925142739025](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925142739025.png)



### ==线程同步（解决线程安全）==

![image-20240925150658230](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925150658230.png)

常见方案：加锁

三个方法：同步代码块

![image-20240925151103523](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925151103523.png)

![image-20240925151838452](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925151838452.png)

```
synchronized (this) {
    if(this.money>=v){
        System.out.println(name+"来取钱"+v+"取钱成功");
        this.money-=v;
        System.out.println(name+"来取钱后，剩余余额："+this.money);
    }else{
        System.out.println(name+"来取钱，余额不足~");
    }
}
```

 同步方法

![image-20240925152210870](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925152210870.png)

![image-20240925152354612](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925152354612.png)

Lock锁

![image-20240925153155376](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925153155376.png)

```
private final Lock lock=new ReentrantLock();

public void drawMoney(double v) {
        String name = Thread.currentThread().getName();
        lock.lock();
        try {
            if(this.money>=v){
                System.out.println(name+"来取钱"+v+"取钱成功");
                this.money-=v;
                System.out.println(name+"来取钱后，剩余余额："+this.money);
            }else{
                System.out.println(name+"来取钱，余额不足~");
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            lock.unlock();
        }
    }
```



线程通信（讲操作系统那个生产者生产完就唤醒消费者消费，消费者消费完又唤醒生产者生产的案例）

![image-20240925155755497](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925155755497.png)



### ==线程池：复用线程的技术==

![image-20240925160531890](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925160531890.png)

![image-20240925160858450](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925160858450.png)

![image-20240925161011301](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925161011301.png)



创建线程池

![image-20240925161308227](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925161308227.png)

![image-20240925161732994](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925161732994.png)

![image-20240925163341448](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925163341448.png)

![image-20240925165350897](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925165350897.png)



线程池执行Runnable接口的线程

![image-20240925165101525](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925165101525.png)



Executors

![image-20240925170615108](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925170615108.png)



==核心线程数量怎么配置？==

![image-20240925171059375](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925171059375.png)

![image-20240925171115486](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240925171115486.png)