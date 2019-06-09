#Java面试题总结

1. 作用域 public,protected,private,以及不写时的区别？

| 作用域    | 当前类 | 同一包内 | 子孙类(不同包) | 其他包 |
| --------- | ------ | -------- | -------------- | ------ |
| public    | ✔️      | ✔️        | ✔️              | ✔️      |
| protected | ✔️      | ✔️        | ✔️              | ❌      |
| default   | ✔️      | ✔️        | ❌              | ❌      |
| private   | ✔️      | ❌        | ❌              | ❌      |

[查看详情](https://www.cnblogs.com/yuanfy008/p/8006604.html)

2. 编程输出如下图形 

```
*****
****
***
**
*
```

```java
public class Print {
	public static void main(String[] args) {
		for (int i = 0; i < 5; i++) {
			for (int j = 5; j > i; j--) {
						System.out.print("*");
			}
			System.out.println();
		}
	}
}
```

3. 在 JAVA 中，如何跳出当前的多重嵌套循环？

   > 用 break; return 方法。

4. 排序都有哪几种方法？请列举。用 JAVA 实现一个快速排序？

   > 排序的方法有：插入排序（直接插入排序、希尔排序），交换排序（冒泡排序、快速排序），选择排序（直接选择排序、堆排序），归并排序，分配排序（箱排序、基数排序）快速排序的伪代码。

5. Tomcat部署方式

   > 1. 非常简单，直接将 web 项目文件（一般是复制生成的war包）复制到tomcat的webapps目录中。
   >
   > 2. 在本地tomcat的conf目录中，新建Catalina/localhost目录（这里要注意文件名的大小写），然后在该目录下新建一个xml文件，名字不可以随意取，要和path后 的名字一致，我这里就应该是jstore.xml文件，它的具体内容为：
   >
   >    ```xml
   >    <Context docBase="C:\work\web" path="/Demo" reloadable="true"/>
   >    ```
   >
   > 3. 在tomcat中的conf目录下的server.xml文件中，在<Host/>节点中添加一个context，具体为：
   >
   >    ```xml
   >    <Context Path="/Demo" Docbase="C:\work\WebContent" Debug="0" Privileged="True" Reloadable="True"></Context>
   >    ```
   >
   >    > 这里的 Reloadable= “true” 这个属性是指tomcat在运行状态下会自动检测应用程序的WEB-INF/classes和WEB-INF/lib目录下的class文件，如果监测到有class文件有改动，服务器自动加载新的web应用程序，可以在不重起tomcat的情况下改变应用程序，也就是热部署； 
   >    >
   >    > 一般我们会在开发阶段将Reloadable属性设为true，有助于调试servlet和其它的class文件，但是由于这样会增加服务器的运行负荷，损耗系统性能，在项目运行阶段建议将它设为false。

6. [MySql两种存储引擎的区别](https://www.cnblogs.com/wangdake-qq/p/7358322.html)

   | MyISAM                                                 | InnoDb                                                       |
   | ------------------------------------------------------ | ------------------------------------------------------------ |
   | 不支持事务，但每次查询都是原子的                       | 支持[ACID](https://baike.baidu.com/item/acid/10738?fr=aladdin)的事务，支持[事务的四种隔离级别](https://www.cnblogs.com/huanongying/p/7021555.html) |
   | 支持表级锁，即每次操作都是对整个表加锁                 | 支持行级锁及外键约束：因此支持写并发                         |
   | 存储表的总行数                                         | 不存储总行数                                                 |
   | 一个myisam表有三个文件：索引文件，表结构文件，数据文件 | 一个InnoDb引擎存储在一个文件空间，也可能为多个，受操作系统大小的限制 |

7. [对AOP (面向切面编程)和OOP (面向对象编程)的了解](https://blog.csdn.net/qq_25827845/article/details/75208354)

   > AOP底层使用动态代理实现。包括两种方式：
   >
   >  1）使用JDK动态代理实现。
   >
   >  2）使用cglib来实现

   > AOP：面向切面编程，通过预编译方式和运行期**动态代理**实现程序功能的统一维护的一种技术
   >
   > 总的来说AOP的好处是：
   >
   > 1. 解耦。切面将非业务代码从各模块抽出来，降低了模块间的耦合度。
   >
   > 2. 切面将不同模块共同的与业务无关的代码封装起来，减少了重复代码。
   >
   > 3. 维护方便，将横切关注点统一到一个模块管理，修改更新方便，不影响其他业务模块。
   >
   > 4. 开发分工合作方便，可安排一个人专门复杂横切模块的开发。
   >
   > 5. 节约成本。AOP出现前，需要编写大量重复代码，无论编码和维护都需要付出不少人力成本。
   >
   > 主要功能：日志记录，性能统计，安全控制，事务处理，异常处理等等。

   > OOP（面向对象编程）针对业务处理过程的**实体**及其**属性**和**行为**进行**抽象封装**，以获得更加清晰高效的逻辑单元划分。目的：解决软件系统的可扩展性，可维护性和可重用性；面向对象的三大特性：封装、多态和继承
   >
   > 面向切面编程，指扩展功能不修改源代码，将功能代码从业务逻辑代码中分离出来。

8. 