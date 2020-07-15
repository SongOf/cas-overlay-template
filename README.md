# Versions

```xml
<cas.version>5.2.x</cas.version>
```

# Requirements

* JDK 1.8+

v1版-实现功能
============================
①HTTPS配置
============================
②添加cas-server-support-rest-authentication
===========================================

cas-server-support-rest-authentication模块中配置cas.authn.rest.uri可以将用户验证转移到另一模块

③添加cas-server-support-rest
===========================================

cas-server-support-rest模块提供APP接入获取ST的一系列接口

④修复用户名中文乱码的bug
===========================================

重写cas-server-support-rest-authentication模块添加UTF-8编码

注：WEB-INF下的lib目录保存在网盘，下载导入即可
链接：https://pan.baidu.com/s/17kEHLQjX4hVf6H9_lUP8Hg 
提取码：zm2n


# HTTPS配置

①生成证书  
keytool -genkey -alias cas -keyalg RSA -keysize 1024 -keypass 123456 -validity 365 -keystore d:\cas.keystore -storepass 123456  
-alias后面的别名可以自定义  
-keypass指定证书密钥库的密码  
-storepass和前面keypass密码相同  
-keystore指定证书的位置  
注：提示输入的“您的名字与姓氏是什么” 必须是域名 其他随意  
②导出证书  
keytool -export -alias cas -keystore d:\cas.keystore -file d:\cas.crt -storepass 123456  
③导入证书到jvm  
keytool -import -keystore %JAVA_HOME%\jre\lib\security\cacerts -file d:\cas.crt -alias cas  
④将证书复制到resources目录下  

### win10启动 注tomcat启动有问题  
build.cmd run  