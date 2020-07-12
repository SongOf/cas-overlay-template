实现功能
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




CAS Overlay Template
============================

Generic CAS WAR overlay to exercise the latest versions of CAS. This overlay could be freely used as a starting template for local CAS war overlays. The CAS services management overlay is available [here](https://github.com/apereo/cas-services-management-overlay).

# Versions

```xml
<cas.version>5.2.x</cas.version>
```

# Requirements

* JDK 1.8+

# Configuration

The `etc` directory contains the configuration files and directories that need to be copied to `/etc/cas/config`.
```bash
/usr/bin/sudo ./build.sh copy
```

# Build

To see what commands are available to the build script, run:

```bash
./build.sh help
```

To package the final web application, run:

```bash
./build.sh package
```

To update `SNAPSHOT` versions run:

```bash
./build.sh package -U
```

# Deployment

- Create a keystore file `thekeystore` under `/etc/cas`. Use the password `changeit` for both the keystore and the key/certificate entries.
```bash
./build.sh gencert
```

- Ensure the keystore is loaded up with keys and certificates of the server.

On a successful deployment via the following methods, CAS will be available at:

* `http://cas.server.name:8080/cas`
* `https://cas.server.name:8443/cas`

## Executable WAR

Run the CAS web application as an executable WAR.

```bash
./build.sh run
```

## Spring Boot

Run the CAS web application as an executable WAR via Spring Boot. This is most useful during development and testing.

```bash
./build.sh bootrun
```

### Warning!

Be careful with this method of deployment. `bootRun` is not designed to work with already executable WAR artifacts such that CAS server web application. YMMV. Today, uses of this mode ONLY work when there is **NO OTHER** dependency added to the build script and the `cas-server-webapp` is the only present module. See [this issue](https://github.com/apereo/cas/issues/2334) and [this issue](https://github.com/spring-projects/spring-boot/issues/8320) for more info.


## Spring Boot App Server Selection

There is an app.server property in the `pom.xml` that can be used to select a spring boot application server.
It defaults to `-tomcat` but `-jetty` and `-undertow` are supported. 
It can also be set to an empty value (nothing) if you want to deploy CAS to an external application server of your choice.

```xml
<app.server>-tomcat<app.server>
```

## Windows Build

If you are building on windows, try `build.cmd` instead of `build.sh`. Arguments are similar but for usage, run:  

```
build.cmd help
```

## External

Deploy resultant `target/cas.war`  to a servlet container of choice.


## Command Line Shell

Invokes the CAS Command Line Shell. For a list of commands either use no arguments or use `-h`. To enter the interactive shell use `-sh`.

```bash
./build.sh cli
```
