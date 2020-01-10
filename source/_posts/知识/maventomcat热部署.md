title: maven+tomcat 热部署
date: '2019-06-11 16:18:19'
updated: '2019-08-07 14:28:58'
tags: [maven, tomcat, 热部署]
permalink: 1560241099787.html
excerpt: maven + tomcat热部署 （主要原因是idea社区版太难了）
categories: 编程
---
### 1.配置tomcat-users.xml

```xml
<role rolename="tomcat"/>
<role rolename="manager"/>
<role rolename="manager-gui"/>
<role rolename="manager-script" />
<role rolename="admin-gui"/>
<user username="admin" password="admin" roles="tomcat,manager,manager-script,admin-gui" />
<user username="tomcat" password="tomcat" roles="manager-gui" />
```
### 2.配置maven setting.xml

在servers节点下添加（username和password与上文一致）：
```xml
<server>
  <id>tomcat7</id>
  <username>admin</username>
  <password>admin</password>
</server>
```

### 3.配置pom.xml  
```xml
<plugin>
			<groupId>org.apache.tomcat.maven</groupId>
			<artifactId>tomcat7-maven-plugin</artifactId>
			  <version>2.1</version>
			<configuration>
				<!-- 端口号，可自定义 -->
				<port>8080</port>
				<!-- 项目访问路径 -->
				<path>/study</path>
				<!-- Tomcat Manager的url访问路径，固定写法 -->
				<url>http://localhost:8080/manager/text</url>
				<!-- Tomcat Manager的用户名和密码 -->
				<username>tomcat</username>
				<password>tomcat</password>
			</configuration>
</plugin>
```

添加相关依赖：
```xml
   <dependency>
            <groupId>org.apache.tomcat</groupId>
            <artifactId>tomcat-servlet-api</artifactId>
            <version>8.5.4</version>
        </dependency>
```

### 4.修改ip访问权限
将 /apache-tomcat-8.5.4/webapps/manager/META-INF/context.xml中的，ip限制去掉

```xml
<Context antiResourceLocking="false" privileged="true" >
  <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="192\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
</Context>
```

### 5.执行部署命令
项目根目录下执行：
```
//第一次
mvn tomcat7:deploy
//之后
mvn tomcat7:redeploy
```

```
//这里我要求先重新打包,并跳过测试,再部署
//第一次
mvn package  -Pdevelop -Dmaven.skip.test=true tomcat7:deploy

//之后
mvn package  -Pdevelop -Dmaven.skip.test=true tomcat7:redeploy
```


### 错误：

#### 1. Failed to execute goal org.apache.tomcat.maven:tomcat7-maven-plugin:2.1:deploy (default-cli) on project study: Cannot invoke Tomcat manager: Connection to http://localhost:8080 refused: Connection refused: connect ->
 
 manager 默认上传war包大小是50M，所以要修改\manager\WEB-INF下的web.xml文件：
```xml
<multipart-config>
      <!-- 50MB max -->
      <max-file-size>52428800</max-file-size>
      <max-request-size>52428800</max-request-size>
      <file-size-threshold>0</file-size-threshold>
    </multipart-config>
```
将这里的52428800修改为：104857600
```xml
<multipart-config>
      <!-- 50MB max -->
      <max-file-size>104857600</max-file-size>
      <max-request-size>104857600</max-request-size>
      <file-size-threshold>0</file-size-threshold>
    </multipart-config>
```