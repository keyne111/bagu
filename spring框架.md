# Spring框架

## 什么是spring框架？

spring框架（spring Framework）是一款开源的轻量级Java开发框架，它是很多模块的集合，比如说IOC和AOP，支持访问数据库，还有集成第三方组件，使用spring框架可以提高我们的开发效率和提高系统的可维护性



## spring包含的模块有哪些？

Core container:核心容器（IOC容器）

AOP：面向切面编程  Aspect:AOP思想的实现，比spring自己实现AOP实现要好

Data Access/: 数据访问和数据集成，  数据访问:做Java与数据库之间关联的，比如JDBC。  数据集成：允许集成其它的数据库访问技术，比如Mybatis

Web:  web相关

Test: 测试相关



## spring,springmvc,spring boot 之间什么关系？

spring是spring framework，它是很多模块集合，比如IOC和AOP，支持访问数据库，集成第三方组件阿。然后springMVC是依靠spring框架的IOC去实现的，它是一个表现层框架，帮助我们开发web程序的，并且springmvc还提供了异常处理器和拦截器，==M是model，V是view，C是controller，这样将数据和显示分离，让我们的开发更加清晰==。然后spring boot是用于简化spring配置的，因为spring框架的使用要么在xml文件，要么在注解里面声明，配置很多且不方便，springboot简化成只在yml或yaml中配置即可，并且spring boot还有起步依赖，辅助功能等，便于我们开发程序



# IOC

## 你了解什么是spring IOC吗？

IOC，控制反转，一种编程思想，原来我们需要自己手动new对象出来，现在把new对象的事情交给外部去做，这个外部是IOC容器，或者叫spring容器也可以，==这样做的好处是解耦合和提高系统的可扩展性，==我们可以用xml文件和注解的方式去使用控制反转

然后IOC还与依赖注入有关系，当IOC容器扫描到两个bean之间存在依赖关系的话，IOC容器会自动绑定关系



## 什么是spring bean?

放在IOC容器里面的对象就是bean，我们通过XML文件，注解去配置bean



## 将一个类声明为bean的注解有哪些？

@Component,@Service,@Repository,@Controller



## @Component和@Bean的区别是什么？

1:@Component定义在类上，@Bean定义在方法上

2：@Component需要被componentscan扫描到才能被spring容器创建，==@Bean则是告诉spring这个方法的返回值是一个bean，需要加载到spring容器中，并且我们引入第三方bean的时候只能用@Bean==



## 注入bean的注解有什么？

@Autowired

@Resource

@Inject



## @Autowired和@Resource的区别是什么？

@Autowired是spring内置的注解，默认按类型匹配，当按类型匹配找不到默认会按名称匹配，如果有多个实现类，可以手动声明@Qualifer注解

@Resource是JDK内置的注解，默认按名称匹配，按名称找不到的话按类型匹配，或者可以通过name属性去配置

@Resource的作用域范围小，只能在方法和字段上声明，不能再构造方法和参数上声明，而@Autowired可以



## 注入bean的方式有哪些？

Setter注入，

构造器注入

自动装配



### 构造函数注入还是 Setter 注入？

官方推荐是构造函数注入，但是我自己感觉在学习的时候使用setter注入会多一点





## Bean的作用域有哪些？

singleton：单例

prototype：非单例

request：每一次HTTP请求创建一个bean

session：每一次session会话创建一个bean

websocket:每一次webSocket创建一个bean

application/global-session :每一次web应用启动创建一个bean



如何配置bean的作用域？

xml文件的scope属性

@Scope注解





## Bean是线程安全的吗？

bean是否线程安全，需要看它的作用域和状态

比如prototype，它每一次创建都会生成一个新的对象，不存在资源冲突，线程安全

而像singleton的话，得看它是否包含可变成员变量的对象，如果包含，存在资源冲突，线程不安全



解决线程不安全的问题的话：

避免可变成员变量

使用ThreadLocal保证线程安全

使用同步机制





## Bean的生命周期了解吗？

1：创建IOC容器

2：执行构造方法把对象放进IOC容器（这些对象也叫bean）

3：依赖注入（setter方法）

4：bean的初始化

5：我们使用bean去执行业务

6：bean的销毁

7：关闭IOC容器



# AOP

## ==谈谈你对AOP的了解？==

AOP：面向切面编程，它的本质是代理模式，如果要代理的对象有实现某个对象，则会用JDK proxy生成一个代理对象，如果没有实现某个对象的话，则会用cligb生成一个被代理对象的子类去代理对象，AOP做的事情是不侵入源代码的情况下增强功能，它与5个东西有关，连接点，切入点，通知类，通知，切面。然后AOP的通知类型有五种，前置，后置，环绕，返回后通知，抛出异常通知。然后如果有多个切面的话，可以通过@Ordered注解配置切面执行顺序，值越小优先级越高，也可以通过实现Ordered接口，重写getOrder方法配置切面执行顺序





## Spring AOP 与 AspectJ AOP的区别？

Spring AOP基于代理模式，属于运行时增强，AspectJ AOP基于字节码操作，属于编译时增强

Spring AOP已经集成AspectJ AOP，AspectJ AOP功能更强大，不过Spring AOP使用简单

如果有多个切面的情况下，使用AspectJ AOP性能会更好



## AOP的通知类型有哪些？

前置：在原始方法执行之前

后置：在原始方法执行之后

环绕：功能最强大，可以做其它四个通知的事情

返回后通知：得到方法的返回值后在执行

抛出异常通知：方法抛出异常才执行



## 多个切面的执行顺序任何控制？

可以在通知类上加@Order()注解，值越小优先级越高

或者在通知类上实现Ordered接口，然后重写getOrder方法，返回值越小也是优先级越高



# spring事务

## spring管理事务的方式有哪几种？

编程式事务和声明式事务。

编程式事务是通过代码硬编码，通过TransactionTemplate或TransactionManager手动管理事务，

声明式事务主要是通过注解，通过@Transactional注解，==它的本质是通过AOP实现==



## spring事务传播行为了解吗？

spring有7种事务传播行为，默认的事务传播行为是事务协调员加入事务管理员

然后我比较熟悉的是另一种了，事务协调员不加入事务管理员，自己创建一个新事务，应用场景的话是记录日志，不管操作成员与否都记录一次日志。

==事务传播行为可以通过@Transactional的propagation属性去配置==

![image-20240911165547556](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911165547556.png)





## Spring 事务中的隔离级别？（不了解）





## @Transactional(rollbackFor = Exception.class)注解了解吗？

这个注解是因为spring事务默认只对Error异常和运行时异常做回滚处理，如果遇到其它异常，比如IOException,Exception，程序默认是不会回滚处理的

然后通过@Transactional注解的rollbackFor属性的话，可用配置让spring事务去处理这些异常



# springMVC

## 谈谈你对springmvc的了解？

springMVC是用于开发web层框架的，是一个表现层框架，它依赖spring框架的依赖注入功能，M是model，v是view，C是controller，springMVC将数据和显示分离开，开发清晰，并且springmvc还提供了异常处理器和拦截器，方便我们对springmvc的请求做处理





## springMVC的核心组件是什么？

DispatcherServlet:核心的中央处理器，负责接收请求，分发，响应客户端

HandlerMapping:处理器映射器，根据请求的url找到对应的handler

HandlerAdaptor:处理器适配器，执行对应的handler

hander:请求处理器，执行实际的方法

ViewResolver:视图解析器，解析结果，返回给DispatcherServlet响应客户端



## springMVC的工作流程？

浏览器发送请求，被DispacherServlet拦截

DispatcherServlet根据请求信息找到对应的HandlerMapping,

HandlerMapping根据请求的url找到对应的Handler

DispatcherServlet调用HandlerAdapter适配器执行Handler

Handler执行完会返回一个ModelAndView对象给DispatcherServlet

ViewResolver会根据逻辑view查找到实际的view，

DispatcherServlet将model返回给view

将view返回给前端



## 统一异常处理怎么做？

springMVC提供了异常处理器，然后我们处理异常的思路是先把异常往上抛出去，抛到表现层再进行集中处理

然后根据异常的分类去做处理，像服务器宕机，联系管理员没问题，但用户输入非法参数异常，还联系管理员，就有问题了。

我们可以将异常分为系统异常，业务异常，未知异常

声明一个异常处理器用@ControllerAdvice或@RestControllerHandler注解，和@ExceptionHandler注解去拦截对应的异常