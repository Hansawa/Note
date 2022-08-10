bin\startup.bat乱码：修改conf\logging.properties的“java.util.logging.ConsoleHandler.encoding”值为GBK

tomcat服务器加载了工程且运行后，将锁定配置，只有移除工程才能进行配置的更改

双击tomcat服务器，修改server locations为“use tomcat installation”使得翻译与编译后的.java与.class文件放在work文件夹里。修改deploy path为“webapps”使得让工程加载到webapps文件夹里