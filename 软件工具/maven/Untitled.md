# Maven

## 是什么

是一款服务于 Java 平台的自动化构建工具

构建：1. 编译 2. 部署 3. 搭建

## 为什么

通过该工具，我们可以将对第三方依赖包的查找、导入与管理等繁琐行为替换成简单的配置工作

## 怎么用

在maven的依赖包搜索网站（如`https://mvnrepository.com/`）输入依赖包名，找到合适的依赖包及其版本，将网站提供的配置标签段复制进pom.xml里，让maven重新构建工程

## 核心概念

1. 约定的目录结构
2. POM
3. 坐标：定位一个 Maven 工程
4. 依赖
5. 仓库
6. 生命周期/插件/目标
7. 继承
8. 聚合

### 约定的目录结构

![image-20210603201456850](C:\Users\Hans\AppData\Roaming\Typora\typora-user-images\image-20210603201456850.png)

## @pom.xml

### #<resource>

maven会将java文件夹中的java文件编译成字节码文件放在target/classes文件夹，并将resources目录的资源文件一同复制进classes文件夹中，然后才是运行程序。为了与eclipse的文件结构相似，可以配置添加新的resources目录，如下。意思为可以在java的包中添加.xml，.properties文件，且maven会在不破坏java包的文件结构（其中包含了资源文件）的情况下，将其放置在target/classes，让程序正确运行.

```xml
<!-- 配置添加新的resources目录 -->
<resources>
    <resource>
        <directory>src/main/java</directory>
        <includes>
            <include>**/*.xml</include>
            <include>**/*.properties</include>
        </includes>
    </resource>
</resources>
```

## @ 指明 maven 目录

idea -> settings -> Build, Execution, Deployment -> Builds Tools -> Maven ->  Maven home path

## @ maven 配置文件 settings.xml 设置

idea -> settings -> Build, Execution, Deployment -> Builds Tools -> Maven ->  User settings file

可以在配置文件里配置镜像网站地址，本地仓库等等

## @ maven 仓库位置设置

idea -> settings -> Build, Execution, Deployment -> Builds Tools -> Maven -> Local repository

