start
=========

配置文件作用：
SpringBoot默认支持properties和YAML两种格式的配置文件。前者格式简单，但是只支持键值对。如果需要表达列表，最好使用YAML格式。
bootstrap.yml 是被一个父级的 Spring ApplicationContext 加载的。这个父级的 Spring ApplicationContext是先加载的，
在加载application.yml 的 ApplicationContext之前。


iml是 intellij idea的工程配置文件，里面是当前projec的一些配置信息

NETFILX CORE组件
----------------
### Feign
 
概念
Feign是一个声明式的伪Http客户端，feign是一个伪客户端，即它不做任何的请求处理。Feign通过处理注解生成request，从而实现简化HTTP API开发的目的，
即开发人员可以使用注解的方式定制request api模板，在发送http request请求之前，feign通过处理注解的方式替换掉request模板中的参数，
这种实现方式显得更为直接、可理解。
 
.首先通过@EnableFeignCleints注解开启FeignCleint
.根据Feign的规则实现接口，并加@FeignCleint注解
.程序启动后，会进行包扫描，扫描所有的@ FeignCleint的注解的类，并将这些信息注入到ioc容器中。
.当接口的方法被调用，通过jdk的代理，来生成具体的RequesTemplate
.RequesTemplate在生成Request
.Request交给Client去处理，其中Client可以是HttpUrlConnection、HttpClient也可以是Okhttp
.最后Client被封装到LoadBalanceClient类，这个类结合类Ribbon做到了负载均衡。

 
 ### Eureka
 ![baidu](http://www.baidu.com/img/bdlogo.gif)
