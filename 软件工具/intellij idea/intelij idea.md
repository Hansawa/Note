[TOC]

创建java enterprise工程来创建动态web工程

可以通过默认设置来让每一个新创建的project遵循该设置

依赖包要添加到添加到项目依赖才能在external libraries中查看，Libraries只是预备库

安装intellij后先不要打开，先设置配置目录，包括插件目录，不要放在c盘，如下图：

![](D:\typora-workspace\软件工具\intellij idea\intellij bin ideaproperties.png)

## @环境搭建

1. 配置jdk（影响单一工程）：`file > project structure > project settings > project > project sdk`
2. 添加tomcat server（影响全部工程）：`file > settings > build execution deployment > application servers`
   - 修改tomcat server的配置（影响单一工程）：`run > edit configurations > 选择相应的tomcat`
3. 解决乱码问题
   1. `Services Tool Window`的tomcat的Server日志出现中文乱码：将`Settings->Editor->Console->Default Encoding`改为GBK，将%TOMCAT_HOME%\conf\logging.properties的`ConsoleHandler`哪一行的值改为GBK
   2. `Services Tool Window`的tomcat的Server中输出java的print语句时中文乱码：将`Settings->Editor->Console->Default Encoding`改为GBK
   3. `Services Tool Window`的tomcat的Catallina Log出现中文乱码：将`Settings->Editor->Console->Default Encoding`改为GBK，将%TOMCAT_HOME%\conf\logging.properties的`CatallinaHandler`那一行的值改为GBK
   4. 原因：Windows控制台默认字符集GBK，而tomcat的日志（他的日志也接收java的print语句）输出是经过windows控制台

## @从头开始一个java web项目

- 使用javaEE规范
- 选择jdk
- 选择工程模板为`Web application`
- 选择web应用服务器（如tomcat）
- 选择构建工具
- 进入工程
- 导入依赖包
  1. 使用maven导入相关依赖包（使用pom.xml）
  2. 自己导包：将所需要的包放进一个lib文件夹里，然后将lib放进webapp的WEB-INF文件夹里，这样build的时候才会将自己导入的包放到war里。而通过modules或libraries导包只能给编写代码时进行提示用，如下一步
- 通过modules的dependencies导入应用服务器依赖包（允许jsp代码提示，不会放进war里）
- 配置运行配置

## @导包方式

1. 使用maven导入相关依赖包（使用pom.xml），要在每个dependency标签里填写scope（包处理方式，有provided，complie，test等），因为在`Project Structure->Modules`中更改`scope`方式是无法影响到依赖包真实的处理方式的
2. 自己导包：将所需要的包放进一个lib文件夹里，然后将lib放进源目录的webapp的WEB-INF文件夹里，这样build的时候才会将自己导入的包放到war里。而通过modules或libraries导包只能给编写代码时进行提示用。源目录的lib如下：

![源目录lib](D:\typora-workspace\软件工具\intellij idea\源目录lib.png)

## @Build功能介绍

1. `Build project`后将会生成放在target目录里的classes目录，该目录存放在java目录里的java文件编译后的字节码与resources目录里的文件（.xml, .properties, .img......）
2. `Build artifacts war`后将会生成放在target目录中的war包
3. `Build artifaccts war: exploded`后将会生成放在target目录中的解压war包后的文件，这些文件的目录结构也为war包的目录结构

## @war与war: exploded模式

1. war模式：这种可以称之为是发布模式，看名字也知道，这是先打成war包，再发布。build后会生成war包；
2. war exploded模式：是直接把文件夹、jsp页面 、classes等等移到Tomcat 部署文件夹里面，进行加载部署。因此这种方式支持热部署，一般在开发的时候也是用这种方式。

## @java web项目目录结构

### #总目录结构

![](D:\typora-workspace\软件工具\intellij idea\javaweb目录结构.png)

1. java目录：放置java文件（会被编译，build编译出字节码后按目录结构放在target目录下的classes目录与target目录下的war（war：exploded）下的WEB-INF目录的classes目录里）
2. resources目录：存放.xml, .properties等文件（build后会按目录结构放在target目录下的classes目录与target目录下的war（war：exploded）下的WEB-INF目录的classes目录里）
3. webapp目录：存放页面文件，web.xml配置文件及自己导包时放在WEB-INF中的lib目录（其中都是自己导的包，不通过maven）
4. test目录：存放java测试文件
5. target目录：存放build后的输出文件
6. pom.xml：maven的用于搭建环境的xml文件
7. external libraries：通过maven与module或libraries导入的包放在这里（maven导的包build后会放入target目录下网站目录下的WEB-INF的lib中，而除了手动放入源目录的lib中，其他方式build后都不会放入target目录的lib里）

### #target目录结构

![image-20210405205143453](C:\Users\Hans\AppData\Roaming\Typora\typora-user-images\image-20210405205143453.png)

1. classes目录：build后，存放由放在java目录下的java文件生成的字节码文件与放在resources目录的.xml, .properties文件，对于这些文件，classes目录作为根目录
2. war：exploded目录：`build war: exploded`后将产生该目录，该目录名字是项目名+版本名，放着war包解压后的目录与文件，相当于直接加载到web服务器，用于开发时web服务器的热部署，一般开发时都会选择build war：exploded。值得注意的是：build war（build war：exploded）后maven导入的依赖包与手动放在源目录的WEB-INF的lib的依赖包将会集合成一个lib目录放到target目录的WEB-INF目录中。WEB-INF目录下的classes目录与1相同。
3. war包：`build war`后将产生该包，整个项目的发布包，该包放到web服务器的webapps中即可以通过网址浏览网站

## @设置服务器热部署

在run/debug configurations中选择相应服务器，将on update action与on frame deactivation的值改为update classes and resources

## @运行单一web页面

- 先启动服务器
- `alt+F2`或点击右上角显示的几个浏览器

## @常用快捷键

1. 重命名：`ctrl+f6`
2. 注释：`ctrl+/`
3. 打开服务窗口：`View->Tool Windows->Services`:`alt+8`
4. 选择一对标签：`ctrl+j`
   - 标签多选：`ctrl+alt+j`
5. 类刷新target：<kbd>ctrl</kbd>+<kbd>F9</kbd>（`build project`） && <kbd>ctrl</kbd>+<kbd>alt</kbd>+<kbd>y</kbd>（`reload all from disk`）
6. 打开上下文菜单：alt + Insert
7. 最大化 terminal：`ctrl`+`shift`+`"`
8. 专注到某一面板：`alt`+`任意面板英文首字母`

## @创建文件模板

`settings > Editor > File and Code Templates`

Tips: 不写`File name`即可在创建该种文件时为其命名

## @生成getter与setter

- 直接查找(shift*2)
- 右键选择generate
- alt+insert键

## @terminal tool window会覆盖ide的快捷键

修改方法：`Settings->Tools->Terminal->弃选Override IDE shortcut`

## @将war包部署到linux服务器上

1. 用cmd的sftp上传文件到linux的tomcat的webapps中，tomcat会自动部署
2. 方法与1类似，只不过是使用idea内置的功能
   - 打开项目前，先`Settings->Build, Excution, Deployment->点击Deployment->添加远程连接，设置Connection(最好将Root Path设置为web服务器放网站的地方如tomcat的webapps)`
   - 打开项目后，找到原先的界面，设置`mappings`，将`Local Path`改成该project下的target目录，将`Deployment Path`改成`/`，这样设置就可以直接使用快捷键上传war包到webapps目录下，而不是将target目录一并传过去
   - 除了使用快捷键，还可以不改`Local Path`，只设置`Deployment Path`为`/`，然后用鼠标将war包拖过去

## @软包装

https://blog.csdn.net/huyuchengus/article/details/112089468

## @使用内置数据库

`View->Tools Windows->database`

## @查看错误日志（比如生成代码所使用的groovy）

`Help->Show Log in explorer`

## @markdown使用plantuml（puml）

- 需要安装Graphviz，并配置环境变量
- `Settings->Languages & Frameworks->markdown`勾选plantUML

## @pom文件变灰，maven不可用

解决方案：`settings->Build, ......->maven->ingnored files->取消选中`

## @创建文件时没有jsp选项

解决方案：`project structure->Modules->web->web resource directories->添加存放web资源的目录`

## @好用插件

1. GIdeaBrowser 内置浏览器
2. background image plus
3. Translation
4. Power Mode II 打字特效
5. Easy Code 代码生成
6. PlantUML integration UML画图

## @临时问题

导出sql文件

pom第一次不自动弹出groupId

## @新建SSM项目

1. 新建空maven项目
2. 删除src目录
3. 引入全局依赖
4. 新建空maven模块
5. 添加web Application框架
6. 引入局部依赖
7. 在项目结构中将jar包导入lib中
8. 在web.xml中配置DispatcherServlet（前端控制器）
9. 创建要被DispatcherServlet绑定的spring配置文件
10. 开启组件扫描
11. 使用mvc默认servlet处理器
12. 开启注解驱动（支持mvc注解）
13. 配置视图解析器（前缀后缀）
14. 创建对应的视图的目录与文件

## @SSM web服务器tips

1. 如果只改了前端页面刷新一下
2. 如果只改了java代码，就reploy
3. 改了配置文件，就要重启tomcat

## @无法返回json数据

解决方案：将tomcat更换为8.X以上

## @idea支持es6语法

`File -> settings -> Lauguages & Frameworks -> javascript -> javascript languages version改为ECMASCript6`

## @如何创建一个可用的空项目

新建一个空项目后，通过将自身作为 module 导入项目即可