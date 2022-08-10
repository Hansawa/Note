# ！IDE：eclipse-jee-kepler-sr1-win32

## @通用

### #Loading class `com.mysql.jdbc.Driver`. This is deprecated. The new driver class is `com.mysql.cj.jdbc.Driver`. The driver is automatically registered via the SPI and manual loading of the driver class is generally unnecessary.

解决方案：将使用的数据库驱动类更改为`com.mysql.cj.jdbc.Driver`

原因：使用的mysql数据库驱动的版本为8.0X版本，该版本的数据库驱动类为`com.mysql.cj.jdbc.Driver`，而之前的版本使用的数据库驱动类为`com.mysql.jdbc.Driver`（或许）

首次出现该问题的环境：mysql5.5，mysql-connector-java-8.0.11，eclipse-jee-kepler-sr1-win32

### # ### Error querying database.  Cause: java.sql.SQLException: The server time zone value `ÖÐ¹ú±ê×¼Ê±¼ä` is unrecognized or represents more than one time zone. You must configure either the server or JDBC driver (via the serverTimezone configuration property) to use a more specifc time zone value if you want to utilize time zone support.

解决方案：在使用的数据库url中添加要传输的参数`serverTimezone=UTC`(传输参数时要在地址后添加`?`，每个参数用`&`拼接)

原因：待定

首次出现该问题的环境：mysql5.5，mysql-connector-java-8.0.11，eclipse-jee-kepler-sr1-win32

# ！IDE：intellij idea

## @通用

#### #ERROR StatusLogger No Log4j 2 configuration file found. Using default configuration (logging only errors to the console), or user programmatically provided configurations. Set system property 'log4j2.debug' to show Log4j 2 internal initialization logging. See https://logging.apache.org/log4j/2.x/manual/configuration.html for instructions on how to configure Log4j 2

解决方案：导入slf4j-log4j12依赖包（待定）

原因：（待定）

首次出现该问题的环境：mysql5.5，mysql-connector-java-8.0.11，intellij idea 2020.3.3

### #数据库时间类型的值与java中查询的值不一致

解决方案：将数据库的url后加上serverTimezone=Asia/Shanghai（这是url参数，要加?）

原因：时区设置问题

首次出现该问题的环境：mysql5.5，mysql-connector-java-8.0.11，intellij idea 2020.3.3

### # Error querying database.  Cause: org.apache.ibatis.executor.ExecutorException: No constructor found in top.hansarchive.pojo.User matching [java.lang.Integer, java.lang.String, java.lang.String]

解决方案：给pojo类加上无参构造方法

原因：mybatis需要调用无参构造方法

首次出现该问题的环境：mysql5.5，mysql-connector-java-8.0.11，intellij idea 2020.3.3

## @非通用

### #使用mybatis连接数据库，sql查找语句使用中文，执行成功，但返回值为空

解决方案：将`settings > Editor > file Encodings`中`project Encoding`的值修改为`UTF-8`

原因：（待定）

首次出现该问题的环境：mysql5.5，mysql-connector-java-8.0.11，intellij idea 2020.3.3

### #使用maven导入第三方依赖包，配置正确但有时会显示没有某些包

解决方案：

1. `右键该工程 > maven > reload project`
2. 点击右侧maven标签，点击弹出窗口左上角的`reload all maven projects`

原因：（待定）

首次出现该问题的环境：mysql5.5，mysql-connector-java-8.0.11，intellij idea 2020.3.3

### #新建的java ee项目运行的第一个页面总是index.jsp

解决方案：在项目的web.xml中设置主页

原理：tomcat启动时，会读取web.xml文件，项目中的web.xml以及tomcat自带的（位置：apache-tomcat-x.x.xx\conf\web.xml），tomcat的web.xml有welcome-file-list

### #jsp代码找不到out等java对象，变红

解决方案：导入tomcat库