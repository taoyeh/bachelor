# 基本概念

JavaWeb=Java+Web

Web:World Wide Web，即全球广域网，也称为万维网，它是一种基于超文本和HTTP的、全球性的、动态交互的、跨平台的分布式图形信息系统。比如：百度，淘宝。
- 静态网页：只有静态资源，数据始终不会发生变化
- 动态网页：动态数据

在Java中，动态web资源开发的的技术栈统称为JavaWeb


# Tomcat
Tomcat 服务器是一个免费的开放源代码的Web 应用服务器，属于轻量级应用服务器，在中小型系统和并发访问用户不是很多的场合下被普遍使用，是开发和调试JSP 程序的首选。**你可以简单将它理解为IIS**，有了tomcat我们就可以访问自己写的网站


![image.png](https://i.loli.net/2021/06/08/o18kQ9zBGs3fmrc.png)
## Tomcat下载
Tomcat 官网 ：[https://tomcat.apache.org/](https://tomcat.apache.org/)

![image.png](https://i.loli.net/2021/06/08/evWjpyoxUbgS5un.png)


## Tomcat启动和关闭

文件夹的信息

![4FSU~Z3X2RCC_NMBOYE_Y~0.png](https://i.loli.net/2021/06/09/BGEJV6FQOMiWpDh.png)

开启和关闭 在bin文件下操作

![image.png](https://i.loli.net/2021/06/09/5J6c2ALtI8UB7Zv.png)


直接访问 [http://localhost:8080/](http://localhost:8080/)  就能访问Tomcat


将自己写好的网站，直接放到服务器（Tomcat）中指定的web应用的文件夹下（webapps）,就可以访问网站应该有的结构


## IDEA 中使用Tomcat

![image.png](https://i.loli.net/2021/06/14/DVye8nmJYSrFdxj.png)



# Maven

**为什么要用Maven**


在JavaWeb开发中，需要使用大量的jre包，需要手动导入

为此需要一个工具帮我们导入和配置jre包

由此 Maven 诞生了！



## Maven是一个架构管理工具

Maven 就是用来方便导入jre包的！

Maven核心思想 ： **约定大于配置**

Maven会规定java的目录结构 按照要求规范


## Maven配置与使用

官网：http://maven.apache.org/


在Download页面中下载
![image.png](https://i.loli.net/2021/06/10/38lVgKqRoQUPDJM.png)


配置maven :在环境变量下

- M2_HOME:  maven 目录下的bin目录（D:\Environment\apache-maven-3.8.1\bin）
- MAVEN_HOME:  maven的目录（D:\Environment\apache-maven-3.8.1）
- 在系统的Path中配置：%MAVEN_HOME%\bin

配置完毕后的情况：

![image.png](https://i.loli.net/2021/06/10/5GWqjupIk9ZTsxH.png)


##  阿里云镜像

使用原因：国外的jar包下载比较慢 所以我们用国内镜像，**加快下载速度**

配置方法：conf 文件下settings.xml 中的mirrors


```
 <mirror>
        <id>nexus-aliyun</id>
        <mirrorOf>central</mirrorOf>
        <name>Nexus aliyun</name>
        <url>http://maven.aliyun.com/nexus/content/groups/public</url>
    </mirror>
```

## 本地仓库


本地仓库：下载jar包的地方（如果不设置自动放在c盘不太好）

```
<localRepository>D:\Environment\apache-maven-3.8.1\maven-repo</localRepository>
```


## IDEA 中使用Maven

新建maven项目
![image.png](https://i.loli.net/2021/06/12/Pcjk42HzodhxSUL.png)
![image.png](https://i.loli.net/2021/06/12/T7QePj2wAsVXuOF.png)


改变项目maven配置

![image.png](https://i.loli.net/2021/06/12/Igo5DxYs7Jyj4ah.png)

# JSP
JSP全名为**Java Server Pages**，中文名叫java服务器页面，是一种动态网页开发技术。**它使用JSP标签在HTML网页中插入Java代码；**