

Mybatis的语句

![image-20240911202151835](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911202151835.png)





# IOC

IOC：控制反转,原来我们需要new对象，现在把new对象的事情交给IOC容器去做，这样做的好处是可以解耦合，用xml,和注解等方式去做控制反转的

IOC容器：负责对象的创建，初始化等一系列工作，在IOC里面的对象叫做Bean,

DI：依赖注入，在IOC容器中，如果两个bean之间有依赖关系，IOC容器给你绑定好

依赖注入有两种方式，setter注入，构造器注入，自动装配（但是自动装配默认  是使用的setter注入，然后按类型帮我们注入）

![image-20240909211126177](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909211126177.png)

配置bean

1：导入一个spring-context的坐标

2：建立一个applicationContext.xml

3：<bean id=""  class=""/>

class是告诉IOC容器要管理哪个对象（bean）

id是配置（bean）名称，根据名称拿到对象（bean）

![image-20240909165035596](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909165035596.png)

获取ioc容器，根据bean的名称拿到对象（bean）

![image-20240909165458883](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909165458883.png)



依赖注入： ref中的“bookDao” 才是配置的bean

![image-20240909170147672](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909170147672.png)

bean别名：name 属性 ，可以设置多个别名，getBean()的时候能用

![image-20240909170444075](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909170444075.png)

bean的作用范围，默认是单例的 。  scope属性配置

![image-20240909170702280](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909170702280.png)

bean是如何创建出来（实例化）的

1：构造方法

2：静态工厂

![image-20240909171852516](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909171852516.png)

3：实例工厂  下面是被spring优化后的，初始的时候是创建一个对象，然后调用对象里面的set方法（传入对象）得到bean

![image-20240909195231343](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909195231343.png)

![image-20240909195248536](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909195248536.png)



bean的生命周期了解吗？

1：创建IOC容器

2：执行构造方法把对象放进IOC容器（这些对象也叫bean）

3：依赖注入（setter方法）

4：bean的初始化

5：我们使用bean去执行业务

6：bean的销毁

7：关闭IOC容器



依赖注入有哪几种方式？

setter注入 ，构造器注入  



自动装配：IOC容器扫描bean，发现bean之间有依赖关系，会给我们注入好引用类型对象（不能自动装配基本类型和String）

自动装配方式：==按类型，按名称==，按构造方法

按类型指的是IOC容器中的BookServiceImpl中需要依赖BookDao或者是它的子类，而IOC容器中有BookDaoImpl，满足条件

![image-20240909204802428](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909204802428.png)

按名称，指的是IOC容器中的BookServiceImpl需要依赖BookDao或者是它的子类，而IOC容器中BookDaoImpl的名称是bookDao，需要与BookDaoImpl中的setBookDao,去掉set，再把B变成小写后的bookDao名称一样

![image-20240909204942417](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909204942417.png)

![image-20240909205057814](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909205057814.png)





spring框架怎么管理第三方的bean？  比如使用druid需要一个DruidDataSource对象，里面需要连接数据库的属性去注入  

怎么知道用setter注入还是构造器注入呢？

只能看里面代码，发现是setter注入 

![image-20240909211126177](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909211126177.png)



spring框架怎么使用properties文件的？

1：让spring能扫描到它

开启命名空间，加载properties文件，读取文件里面的属性

![image-20240909212522049](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909212522049.png)





IOC容器（看一下就好了，不重要）

BeanFactory是所有IOC容器的父接口 ，创建的容器是懒加载的（bean的初始化部分）

创建IOC容器：1：类路径下的，2：绝对路径下

![image-20240909222908771](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240909222908771.png)

获取bean对象

getBean()的三个重载方法





使用注解定义bean(做了两件事，1：定义bean，2：让spring容器能扫描到)

@Component:有三个衍生注解（@Service,@Repository,@Controller）

1：定义bean

==@Component它代表了xml文件中的（只代表这个，那些xml文件其它东西靠@Configuration和@ComponentScan("com.itheima")）==

![image-20240911095916174](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911095916174.png)

2：让spring容器能扫描到

![image-20240911100714549](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911100714549.png)





纯注解方式的话

==@Configuration代表了一个原来的ApplicationContext.xml文件====，声明它的类也会被spring容器扫描，这个类也会被加载==

==@ComponentScan("com.itheima")代替了原来ApplicationContext.xml里面的<context:conponent-scan base-package="com.itheima" >==

![image-20240910135043460](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910135043460.png)

![image-20240910135136121](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910135136121.png)

![image-20240910135337309](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910135337309.png)

![image-20240911173301458](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911173301458.png)

排除不需要被加载的bean



==@ComponentScan为什么要写这么细节？写个大的范围不行吗？到springmvc会说==

主要是避免加载到不该让它加载的

比如MVC的bean，就不用让他加载





bean注解的时候作用范围同样是单例 ，@Scope配置

![image-20240910135902563](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910135902563.png)



==注解方式的自动注入==（引用类型的）@Autowired（内部通过==反射==， ==按类型==  注入的）

​									@Qualifer("bookDao2") //当类型有多个，写这个注释手动按名称装配 （它必须先写上 @Autowired才能用，不能单独用）

![image-20240910142147245](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910142147245.png)

注解方式，简单类型的自动注入

![image-20240910142530568](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910142530568.png)

==如果是要通过配置文件的形式（properties文件，yml文件这种）注入值==

@PropertySource("classpath:jdbc.properties")  //让spring容器能扫描到

![image-20240910142845851](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910142845851.png)

![image-20240910143045181](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910143045181.png)



注解方式管理第三方bean

同样需要

比如使用druid需要一个DruidDataSource对象，里面需要连接数据库的属性去注入  

@Bean：表示当前方法的返回值是一个bean

![image-20240911095214594](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911095214594.png)

![image-20240910145622601](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910145622601.png)



第三方bean怎么做到依赖注入的？

简单类型

![image-20240910150401486](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910150401486.png)

==引用类型的注入，在@Bean注解的方法形参写上一个bean（需要被ioc容器扫描到并放到容器里面）==

![image-20240910150425791](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910150425791.png)



# AOP

AOP：面向切面编程，不侵入源代码的情况下做代码增强功能。与连接点，切入点，通知，通知类，切面有关。==AOP的本质是代理模式==

1：写一个类（通知类），类上加@Component,告诉spring容器这是一个bean，@Aspect   告诉spring容器用来做AOP的，扫描类里面的注解

2：切入点 （在哪些方法做增强操作）

3：通知  （具体的增强操作做什么）

4：绑定切入点和通知

5：开启@EnableAspectJAutoProxy  启动@Aspect  注解



工作流程

1：Spring容器启动

2：读取有使用到的切入点

3：初始化bean，看看切入点配的方法是否能至少匹配到一个方法，如果不能，获取bean执行业务方法；如果能，创建原始对象的代理原先，根据代理对象的运行模式运行原始方法与增强的内容完成操作



切入点表达式

![image-20240910205045731](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910205045731.png)



AOP通知类型（5种）

（返回后通知和抛出异常后通知，知道一下就好）

前置通知 @Before

后置通知 @After

环绕通知 @Around ,注意方法参数需要有ProceedingJoinPoint ,如果要增强的方法里面有返回值，则这个方法返回值为Object

![image-20240910211215486](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240910211215486.png)



AOP通知获取参数

```
Signature signature = point.getSignature();
signature.getDeclaringType();//得到类目录
signature.getName();//得到方法名
Object[] args = point.getArgs(); //得到方法参数
```



# spring事务

事务：在数据层保障一系列的数据库操作同成功同失败

spring事务：在数据层或业务层保障一系列的数据库操作同成功同失败,用的JDBC



两个角色：

事务管理员：理解成主事务

事务协调员：理解成分支事务就好

主事务进行回滚，分支事务做加入主事务的事情就好



==spring事务只对两种异常做处理，Error和运行时事务（RuntimeException），如下图==

![image-20240911163139937](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911163139937.png)

==，如果想对其它事务也进行处理的话，用rollbackFor属性指定==

![image-20240911163233965](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911163233965.png)



==事务的传播行为：==

事务要不要加入主事务？默认是选择加入主事务的

如果不想加入主事务

![image-20240911163414863](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911163414863.png)



spring事务使用步骤

1：在接口方法或  类（接口）上写上@Transactional   ，在类上面写则代表这个类的方法都有spring事务

![image-20240911155858549](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911155858549.png)

2：事务管理器（第三方bean）  ，需要依赖注入数据源（DataSource）

![image-20240911160119182](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911160119182.png)

3：告诉spring容器允许使用事务

![image-20240911160232340](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911160232340.png)





# SpringMVC

是什么东西？做web层，表现层框架

为什么要有？servlet开发太麻烦了，简化servlet用的

怎么用？controller  service   model    +restful风格



学什么东西？请求于响应相关，restful



@EnableWebMvc：将前端传来的json数据转成对象

@ResponseBody: 设置当前控制器返回值作为响应体

# Restful

## GET请求发送普通参数

==前端传 ：?name=itcast&age=15==

==Controller类中的方法形参用(String name,int age)==

==前端发送的是name,后端方法也必须要用String name才能够做映射，接收到==

==不然就要用@RequestParam("name")指定前端发的是什么==

![image-20240911175143986](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911175143986.png)

![image-20240911175434058](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911175434058.png)

下面这个知道下，因为业务开发都是用@RequestBody

![image-20240911180130227](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911180130227.png)



## 前端传过来JSON数据

![image-20240911190959757](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911190959757.png)

![image-20240911191115737](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911191115737.png)

![image-20240911191217591](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911191217591.png)

![image-20240911191308870](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911191308870.png)

![image-20240911191319292](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911191319292.png)



Content-Type里面放的东西

![image-20240911191643408](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911191643408.png)



传递日期格式，内部是依靠一个Convert接口

![image-20240911191942406](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911191942406.png)



## RESTful进行开发

![image-20240911195311932](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911195311932.png)



==@PathVariable 在这里体现的==  

![image-20240911195713036](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911195713036.png)



==@RestController  这个注解把@Controller 和 @ResonseBody 的功能聚合了==



![image-20240911200719048](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911200719048.png)



## ==统一返回结果==

尾号为1代表成功，为0代表失败  

查询查成功，返回数据即可，

查询查失败，返回null还要返回一个消息提示

![image-20240911202636090](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911202636090.png)

==要用到构造方法    和    所有属性对应getter和setter方法==

![image-20240911203014201](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911203014201.png)



## ==全局异常处理器==

所有异常都往上抛，不要处理

数据层抛到业务层，业务层抛到表现层  到表现层去处理

这时候有问题了

服务器宕机，联系管理员    √

输入非法参数，联系管理员 ×

所以我们要分类处理，  如果在表现层处理异常，每个方法中单独书写，代码书写量巨大且意义不强，如何解决？AOP思想



SpringMvc想到了这个东西，给我们提供了异常处理器：可用集中，统一处理项目中出现的异常







![image-20240911205149735](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911205149735.png)



@RestControllerAdvice : 处理rest风格开发的controller,类需要被加载到IOC容器中

@ExceptionHandler :告诉SpringMvc你处理什么异常，然后可以在方法的参数接到这个异常



系统异常：比如服务器停电宕机，docker下的数据库突然关闭，数据全没了。也是可预计，但无法避免

其它异常：根本想不到的异常

![image-20240911211145340](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911211145340.png)



==处理方案，反正有问题就先甩锅，再看看是不是自己的代码问题==

![image-20240911211658374](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911211658374.png)

以下就是三类异常

![image-20240911212920809](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911212920809.png)

![image-20240911213127771](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911213127771.png)





![image-20240911213334563](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911213334563.png)

![image-20240911213506898](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911213506898.png)



系统异常可以抽成AOP，嫌麻烦的话直接catch一个SystemException就可以

```
/**
 * 外部接口调用check
 *
 * @yx8102 2020/5/15
 */
@Slf4j
@Aspect
@Component
public class RpcCheckAspect {

    @SneakyThrows
    @Around("@annotation(rpcCheck)")
    public Object around(ProceedingJoinPoint point, RpcCheck rpcCheck) {
        Object result;
        try {

            // 拼装接口入参, 入参名称-入参值map
            Map<String, Object> paramMap = new HashMap<>();
            Object[] paramValueArr = point.getArgs();
            String[] paramNameArr = ((MethodSignature) point.getSignature()).getParameterNames();
            for (int i = 0; i < paramValueArr.length; i++) {
                Object paramValue = paramValueArr[i];

                if (Objects.isNull(paramValue) || paramValue instanceof HttpServletRequest || paramValue instanceof HttpServletResponse) {
                    continue;
                }

                if (paramValue instanceof MultipartFile) {
                    paramValue = ((MultipartFile) paramValue).getSize();
                }
                paramMap.put(paramNameArr[i], paramValue);
            }

            log.info("调用[服务]:{} {} {} {},[参数]:{}", rpcCheck.serviceNameCN(), rpcCheck.serviceNameEN(), rpcCheck.methodNameCN(), rpcCheck.methodNameEN(), rpcCheck.printParam() ? JSON.toJSONString(paramMap) : point.getArgs().length);
            Stopwatch stopwatch = Stopwatch.createStarted();
            result = point.proceed();
            log.info("调用[服务]:{} {} {} {},[返回]:{}", rpcCheck.serviceNameCN(), rpcCheck.serviceNameEN(), rpcCheck.methodNameCN(), rpcCheck.methodNameEN(), JSON.toJSONString(result));
            log.info("调用[服务]:{} {} {} {},[耗时]:{}", rpcCheck.serviceNameCN(), rpcCheck.serviceNameEN(), rpcCheck.methodNameCN(), rpcCheck.methodNameEN(), stopwatch.elapsed(TimeUnit.MILLISECONDS));

        } catch (NullPointerException e) {
            log.error("调用[服务]:{} {} {} {} 异常", rpcCheck.methodNameCN(), rpcCheck.serviceNameEN(), rpcCheck.serviceNameCN(), rpcCheck.methodNameEN(), e);
            throw new SystemException(String.format("[服务]: %s,调用发生异常(无可用服务): %s", rpcCheck.methodNameEN(), e.getMessage()));
        } catch (Exception e) {
            log.error("调用[服务]:{} {} {} {} 异常", rpcCheck.methodNameCN(), rpcCheck.serviceNameEN(), rpcCheck.serviceNameCN(), rpcCheck.methodNameEN(), e);
            throw new SystemException(String.format("[服务]: %s,调用发生异常: %s", rpcCheck.methodNameEN(), e.getMessage()));
        }

        if (Objects.isNull(result)) {
            throw new SystemException(String.format("[服务]: %s, 返回为null", rpcCheck.methodNameEN()));
        }

        return result;
    }

}
```



## ==拦截器==

过滤器可以做多层，访问方法之前，比拦截器还要前面。

拦截器则可以在方法前后都做，可以阻止方法的执行，和AOP不一样，因为AOP是会执行方法的，虽然也可以在方法前后做事情。

过滤器和拦截器之间的区别

![image-20240911215610568](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911215610568.png)

![image-20240911214841341](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911214841341.png)

![image-20240911220748666](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911220748666.png)

![image-20240911220854867](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911220854867.png)

![image-20240911220944242](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911220944242.png)

==设置拦截路径，不设置的话默认拦截所有路径==

执行流程

![image-20240911221235273](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911221235273.png)

请求参数

![image-20240911221528613](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911221528613.png)

![image-20240911221713197](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911221713197.png)

拦截器链

![image-20240911222037051](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240911222037051.png)



# Maven多模块创建

在自己的电脑install安装完被依赖的模块（比如common模块），只能自己的电脑上去引入依赖（其它模块引入common模块），其它的开发者用不了阿，怎么解决？

用到私服去解决





多模块创建

![image-20240912105734551](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912105734551.png)

==02的模块需要用到03的domain下的实体类，在02的maven引入依赖，并且03的需要install进maven仓库才能被扫描到==

![image-20240912105854273](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912105854273.png)



==依赖管理==

![image-20240912111724036](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912111724036.png)

有间接依赖的话，不用再引入直接依赖了。

然后项目同一个依赖版本可能会比较奇怪，由于这个间接依赖阿



可选依赖：不想被别人用；

![image-20240912112543211](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912112543211.png)

排除依赖：我不想用别人的

![image-20240912112610597](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912112610597.png)



聚合： 同时管理多个模块，多个模块作为整体，操作的时候同操作（compile的时候多个模块都compile，确保能同时使用）

![image-20240912112900584](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912112900584.png)

例子  聚合工程打包方式是pom, 还要设置模块名称

![image-20240912113419321](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912113419321.png)

![image-20240912113107973](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912113107973.png)



继承：简化配置（子类可以继承父类的依赖），减少版本冲突（所有继承的子模块统一用同一个版本）

继承是在子类中做的，写上这东西就说明继承了某个模块（能够拥有父类提供的（通用的，共有的）依赖）

![image-20240912140753940](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912140753940.png)

例子：

这时会有一个问题，如果我的2，4两个子模块要用到junit,3不需要用到junit的话，要怎么办？

父类提供了一个可选择的依赖资源,==放在这里面的依赖就是子类自己可以选择要不要继承的依赖==

==还可以基础依赖的子依赖，父工程使用了spring cloud 子类直接使用spring cloud里面自己需要用的依赖就可以==

```
<dependencyManagement>
</dependencyManagement>
```



比如说父类可选数据库驱动包

![image-20240912141148591](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912141148591.png)

==子类中继承的话，自己在子类中的依赖添加，但是千万注意不要加上版本号==

![image-20240912141226318](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912141226318.png)



属性的使用

![image-20240912141556843](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912141556843.png)

![image-20240912141632706](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912141632706.png)



版本知识

![image-20240912142047023](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912142047023.png)



跳过测试

![image-20240912142523173](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912142523173.png)



不跳过测试，但是排除一些不需要去测试的

![image-20240912142442103](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912142442103.png)

# spring boot

spring boot为什么好用？

继承

starter



spring boot优点

自动配置，起步依赖starter（里面包含一堆依赖的版本最佳实践），辅助功能（内置tomcat）



不想要一个功能的时候，排除依赖，再自己添加依赖



下面这个插件，打jar包（jar包包含tomcat，idea的依赖）用的，并且提供一个入口程序

![image-20240912104707615](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912104707615.png)



读取yml中的数据（第三种比较常用，第一第二种了解即可）

![image-20240912150049756](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912150049756.png)

![image-20240912145803787](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912145803787.png)



# 怎么创建微服务项目？（主要是第一个，第二个将就看就行）

[Idea-创建微服务项目_idea创建微服务项目-CSDN博客](https://blog.csdn.net/u010365717/article/details/104814524)

[在idea中搭建微服务项目(22版),详细教程_idea创建微服务项目-CSDN博客](https://blog.csdn.net/weixin_68926017/article/details/131788660)



先在要创建的文件夹下创建一个maven项目，然后，删除到剩下.idea和pom.xml，packaging写pom，然后就添加模块，做聚合模块，然后父子模块关系之类

![image-20240912115620866](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912115620866.png)

添加模块

![image-20240912115921929](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20240912115921929.png)