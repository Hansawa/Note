spring boot 是 spring 的快速开发版本，简化配置，多种微服务

**spring是一个轻量级的，控制反转，面向切面的框架**

**spring是为了解决企业级应用开发的复杂性而创建的，简化开发**

**spring的优点：**

![image-20210413170606223](C:\Users\Hans\AppData\Roaming\Typora\typora-user-images\image-20210413170606223.png)

spring的缺点：发展太久，违背了原先的理念：简化开发复杂度，成了配置地狱

重点：IoC，AOP

**spring的七大模块：**

![image-20210413171009371](C:\Users\Hans\AppData\Roaming\Typora\typora-user-images\image-20210413171009371.png)

大多数公司都在使用springboot！！学spring boot必须要学完spring与springMVC

**spring boot**

- 快速开发的脚手架
- 基于它可以快速开发一个微服务
- 约定大于配置！

**spring cloud**

- 基于springboot实现的，整合spring boot的微服务的

IOC创建对象的方式（有参构造创建对象即包含构造器注入）

![image-20210413224525584](C:\Users\Hans\AppData\Roaming\Typora\typora-user-images\image-20210413224525584.png)

依赖注入：

![](C:\Users\Hans\AppData\Roaming\Typora\typora-user-images\image-20210414100408000.png)

Bean的自动装配

在spring有三种装配方式

1. 在xml显式装配
2. 在java显式装配
3. 隐式自动装配【重点】
   1. byName：保证所有beanid唯一，并且与set方法的参数名一致
   2. byType：保证所有beantype唯一
   3. 使用注解自动装配

### #注解

@Component

@alue

@Scope

…………

xml与注解的最佳实践

1. 用xml来管理bean
2. 用注解来属性注入