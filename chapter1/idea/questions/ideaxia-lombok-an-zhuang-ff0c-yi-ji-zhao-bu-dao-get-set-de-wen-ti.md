# IDEA下lombok安装,@Data get,set找不到的问题

* #### [原文访问链接](https://blog.csdn.net/xzp_12345/article/details/80268834)

* #### Idea下安装lombok\(需要两步\)

* > * ####   第一步： pom.xml中加入lombok依赖包

```
<!-- https://mvnrepository.com/artifact/org.projectlombok/lombok -->
    <dependency>
      <groupId>org.projectlombok</groupId>
      <artifactId>lombok</artifactId>
      <version>1.16.20</version>
      <scope>provided</scope>
    </dependency>
```

* > * #### 第二步：加入lombok插件

步骤：File ——》Settings——》Plugins.    搜索lombok，点击安装install。然后会提示重启，重启。

* #### 解决编译时无法找到set和get 的问题
* > * #### IDEA的编译方式选项错误，应该是javac，而不是eclipse。

                 因为eclipse是不支持lombok的编译方式的，javac支持lombok的编译方式。![](/assets/q1.png)

> * #### 没有打开注解生成器Enable annotation processing

![](/assets/q2.png)

> * #### pom.xml中加入的lombok依赖包版本和自动安装的plugin中的lombok依赖包版本不一致

因为我们添加的lombok插件plugin，点击insall时是自动安装的最新版本的lombok。

但是在pom.xml中的依赖包是maven中的低1.16.20的一个依赖包，版本不一致，造成了无法找到set和get.



