
#### 1.Jenkins插件入门

> https://www.jenkins.io/zh/doc/developer/tutorial/prepare/

1.将生成与 Jenkins 有关的几个项目原型中的一个，hello-world。
    mvn -U archetype:generate -Dfilter=io.jenkins.archetypes:

2.校验仓库依赖
    mvn verify

3. Maven HPI 插件用于构建和打包 Jenkins 插件。 它还提供了一个使用插件运行 Jenkins 实例的便捷方式:
   mvn hpi:run

4. Web 浏览器并查看插件的功能
   http://localhost:8080/jenkins/

=================

#### 2.Log Parser Plugin

> 官方文档：http://wiki.jenkins-ci.org/display/JENKINS/Log+Parser+Plugin

> 代码仓库地址：git@github.com:jenkinsci/log-parser-plugin.git
* 1. 本地运行mvn -X 查看mvn全局配置文件：/usr/local/apache-maven-3.8.6/conf/settings.xml。增加mirror。
```
<mirror>
    <id>alimaven</id>
    <mirrorOf>central</mirrorOf>
    <name>aliyun maven</name>
    <url>https://maven.aliyun.com/nexus/content/repositories/central/</url>
</mirror>
```
* 2.修正Log Parser Plugin仓库中pom.xml文件。

```
<repository>
    <id>central</id>
    <url>http://maven.aliyun.com/nexus/content/repositories/central</url>
</repository>


<pluginRepository>
    <id>central</id>
    <url>http://maven.aliyun.com/nexus/content/repositories/central</url>
</pluginRepository>
```

* 3. 修正target/apache-maven-3.0.1/conf/settings.xml 中自带mvn全局文件。解决central由http变成https访问。

```
<mirror>
    <id>alimaven</id>
    <mirrorOf>central</mirrorOf>
    <name>aliyun maven</name>
    <url>https://maven.aliyun.com/nexus/content/repositories/central/</url>
</mirror>
```