title: mircoservices(微服务)
date: '2019-06-11 16:24:48'
updated: '2019-08-07 14:27:20'
tags: [微服务]
permalink: 1560241487915.html
---
# what are mircoservices
A microservice is an engineering approach focused on decomposing applications into single-function modules with well-defined interfaces which are independently deployed and operated by small teams who own the entire lifecycle of the service. Microservices accelerate delivery by minimizing communication and coordination between people while reducing the scope and risk of change. 

# Iaas Paas Saas 


### Iaas (Infrastructure as a service)

 提供基础服务
===> virtualization servers storage networking 


### Paas(Platform as a service )

提供平台服务
===> runtime middleware o/s



### Saas(Software as a service)
 提供软件服务
===> code data

## Characteristics 

### different of traditional service

#### where to place business logic

Microservices: business logic should reside at the endpionts.

#### the way data is managed 

Microservices: each application should store its data in the most appropriate way .Each instance of a service should be responsible  for it's own data and it's own way of persisting that data.

#### Integration

CI: Continues Integration 。持续集成
CD：Continues Deployment 。 持续部署。
Blue-Green deployment : 蓝绿部署。

![image154502700861720181217141009504.png](https://img.hacpai.com/file/2019/06/image154502700861720181217141009504-e96a45e5.png)
![image154502702396320181217141024933.png](https://img.hacpai.com/file/2019/06/image154502702396320181217141024933-097bc3a7.png)


### Failure

circuit breaker: 用户申请由circuit breaker转发至服务器，如果没有返回结果，circuit breaker返回错误给用户。
 
## Comunication 

### Api

服务间通过api进行通讯。

### Synchronous Asynchronous 

同步： request等待response返回。
异步：request向请求消息队列发送请求，该请求会在某一时刻被端点服务拉出。同理，response消息返回队列也是如此。

### Registry

创建微服务实例时，会进行注册，在注册表中记录有关信息。（不能进行自我注销）

#### Self-registration

创建服务实例时，会调用注册表记录有关信息。 缺点：需要额外的代码调用注册表提供自身信息，删除实例时取消注册。失效时无法自行注销

#### Third-party registration
启动实例并将其记录在注册表内，定期轮询是否响应正确，响应失败在注册表中标记。

### Discovery

#### Client-side discovery

客户端访问注册表，找到实例地址，访问实例地址。
缺点：客户端被运行访问注册表信息，如果注册表在防火墙后，也必须给客户端权限。客户端需要发送两个请求，先请求访问注册表，再发送请求访问实例。

#### Server-side discovery
客户端访问API网关，前端服务根据api找到实例，并调用实例返回。同时api网关还可以实现缓存，减少延迟。