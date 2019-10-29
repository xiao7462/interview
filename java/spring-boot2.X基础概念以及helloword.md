[toc]
# spring boot介绍
spring boot历史，背景网上很多，就是一个快速开发企业级web项目的框架，后续再补与spring MVC 和spring的区别






# helloworld以及项目结构介绍
## IDEA中创建spring boot项目
IDEA中创建  File -> New -> Project
![enter description here](https://i.loli.net/2019/10/29/SIdVuC5Xmkgc2DM.png)

> 版本：java : 10.0.2    IDEA: IDEA(Ultimate Edition) 2019.2.3 学生注册版

> 没有spring initializer的需要在插件里安装spring boot插件
![enter description here](https://i.loli.net/2019/10/29/lm7IPkUWtqBbMgv.png)

点击next
>  sprint  boot  连接不上的原因: 报错为`Cannot download https://start.spring.io;Status:403`      
解决方法： 开手机热点，电脑连接手机热点

修改好信息
![enter description here](https://i.loli.net/2019/10/29/34yFMiQSJARWe8O.png)

依赖选择 spring web
![enter description here](https://i.loli.net/2019/10/29/IoibBEd4Ltle7fJ.png)

创建完成后，可以删除一些不必要的文件
![enter description here](https://i.loli.net/2019/10/29/SfwAu9RIBQbmWEZ.png)

## Hello World示例程序

将application.properties改成application.yml。yml文件和properties配置文件具有同样的功能。二者的区别在于：

* yml文件的层级更加清晰直观，但是书写时需要注意格式缩进对齐。yml格式配置文件更有利于表达复杂数据结构的配置。比如：列表，对象（后面章节会详细说明）。
* properties阅读上不如yml直观，好处在于书写时不用特别注意格式缩进对齐。

application.yml 文件里可以修改打开网页的端口
```yml 
server:
  port: 8888   # web应用服务端口
```
在pom.xml中加入
```xml
<dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

在 src -> mian -> java > com.xxxx.bootlauch 下创建一个 controller文件夹
创建一个`HelloController`的类，输入
```java  
@RestController
public class HelloController {
    @RequestMapping("/hello")
    public String hello(String name) {
        return "hello world, " +name;
    }
}
```
点击启动后，在浏览器输入 http://127.0.0.1:8080/hello 可以得到
![enter description here](https://i.loli.net/2019/10/29/BufaxKPOjcoqUrh.png)




# 项目结构目录简介
![enter description here](https://i.loli.net/2019/10/29/lUImuLzSjCKpXGO.png)
项目结构目录整体上符合maven规范要求：

![enter description here](https://i.loli.net/2019/10/29/FrjMGBy5x1D928U.png)

* src/main/resources/static主要用来存放css、图片、js等开发用静态文件
* src/main/resources/public用来存放可以直接用于访问的html文件
* src/main/resources/templates用来存放web开发模板文件





# 参考
1. [手摸手教你学spring boot 2.x](https://www.kancloud.cn/hanxt/springboot2/1303811)
2.《深入浅出Spring Boot 2.x》
3. [2019年8月新版Spring boot2.0全套视频教程](https://www.bilibili.com/video/av62047875/?p=7)
