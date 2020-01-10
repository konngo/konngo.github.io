title: maven打包出现错误
date: '2019-06-11 16:19:48'
updated: '2019-08-07 14:27:47'
tags: [maven, package]
permalink: 1560241188256.html
excerpt: maven打包出错
categories: 编程
---
### 1.程序包com.sun.xml.internal.ws.spi不存在

解决方法:
	在maven-compiler-plugin下配置configuration：
	
``` xml
		<plugin>
               <groupId>org.apache.maven.plugins</groupId>
               <artifactId>maven-compiler-plugin</artifactId>
               <version>2.1</version>
               <configuration>
                   <compilerArguments>
                       <verbose />
                       <bootclasspath>${java.home}/lib/rt.jar;${java.home}/lib/jce.jar</bootclasspath>
                   </compilerArguments>
               </configuration>
       </plugin>
```


### 2.致命错误：在类路径或引导类路径中找不到软件包 java.lang

解决方法 ：
	注意上文bootclasspath配置：在linux环境下，${java.home}/lib/rt.jar;${java.home}/lib/jce.jar之间用:分开，而在windows环境下，使用;分开。
	
### 3.MojoFailureException 错误

maven默认jdk版本与系统jdk版本冲突，在properties下添加：

``` xml
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
```

或者修改maven的settings.xml文件。

### 4.NoGoalSpecifiedException

在pom.xml中build节点下添加：

```xml
<defaultGoal>compile</defaultGoal>
```