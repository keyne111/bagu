lambda表达式本质：作为接口的实例（其中这个接口只能有一个抽象方法，这种接口也叫函数式接口，不管有没有加@FunctionalInterface注解）

怎么认出是lambda表达式？

   参数列表 -> 方法体

参数列表的类型可以省略（因为有类型推断），当参数列表只有一个的时候,如(o1)直接省略小括号变成o1

方法体的话，如果内容只有一句，可以省略{}和return  如{ return o1+o2; };  可以变成o1+o2



个人认为标准写法，感觉这样最容易认出来

 (o1,o2) ->  {

​	sout("哈哈");

​	sout("哈哈");

​	return o1;

}

一些可以简写成为

s -> sout("哈哈");



lambda表达式进阶：

1：方法引用：（lambda表达式的语法糖，但是感觉没必要学，因为有那个idea的插件工具可以帮我们去转换成方法引用，而且这样可读性好差，只要自己能认得出就可以）

对象：：非静态方法

类：：静态方法

==上面两种情况才适用==：==准备要简化的那个方法的形参列表和返回值====类型==要和==接口中的抽象方法的形参列表和返回值类型一致==

参数列表 -> ==方法体==	主要是看这个方法体是否还能在被其它方法调用

比如

```
Consumer<String> con1= s -> System.out.println(s);//这里的System.out.println(s);可以简化成PrintStream对象.println(s)
所以可以变成
        PrintStream ps = System.out;
        Consumer<String> con2 = ps :: println;
```



第三种情况

类：：非静态方法

没必要记，用不到的



2：构造器引用,跟方法引用类似

Employee :: new;

3：数组引用

String[] :: new;