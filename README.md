
## 简介
  
`Cubic` Cubic 分布式监控，以agent的方式无侵入接入应用，提供各种指标，动态线程堆栈追踪，完整集成arthas功能模块，致力于应用级监控，帮助开发人员快速定位问题

 
因为很多公司使用监控需要进行定制化开发，Cubic 可作为一种技术参考，希望给大家带来些许启发。
 
技术体系：
- 基于Spring Boot 整体技术栈
- 认证模块是基于Spring Boot Security JWT 技术
- WebShell 基于 Vue Xterm 、Websocket、Netty 技术
- Proxy 与 agent 通信基于Netty 、GRPC

 
## 文档
- [快速开始](docs/cn/quick_start.md)
- [远程主机命令下发（动态arthas）](docs/cn/arthas_tools.md)
 
## 结构
 - cubic-agent       应用数据采集agent   
 - config            存放agent配置文件                                                                           
 - cubic-proxy       代理应用，用于接收agent数据，图形化操作等               
 - cubic-ui          页面UI，提供前端各种功能展示,打包完 将dist目录数据拷贝到cubic-proxy  
 - docs              文档   
 - scripts           包含打包脚本、启动脚本         

 - agent-dist         存放打包后的agent完整组件              
 - agent-proxy-dist   存放打包后 proxy 部署 jar                    
 - arthas-dist        用于支持arthas命令集                                                          


## 安装
0.  执行cubic-proxy -> resources -> db -> init.sql 创建表
1.  git clone https://gitee.com/sanjiankethree/cubic.git
2.  执行./mvnw clean package  -DskipTests 或 执行打包脚本 ./scripts/build.sh
3.  打包完成的agent 在agent-dist目录下
4.  打包完成的proxy 在agent-proxy-dist目录下
5.  拷贝agent-dist目录下的agent jar 路径，比如：/user/xxx/cubic-agent.jar
6.  修改agent-dist/config 下的agent.config 的参数agent.arthas_path为agent-dist/arthas/arthas-agent.jar   路径 
7.  如使用IDEA 测试，在测试应用中加入配置 VM option 参数 如下：

```
-javaagent:/user/xxx/cubic-agent.jar  -Dcubic.agent.service_name=cubic-proxy
```

## 功能展示

#### 实例列表（展示当前实例信息）
  ![实例列表](https://images.gitee.com/uploads/images/2020/1209/151947_4d29e334_1168339.png "屏幕截图.png")

#### 基础信息（点击实例-》展示当前实例的基础信息）
![基础信息](https://images.gitee.com/uploads/images/2020/1209/152029_3ccd704e_1168339.png "屏幕截图.png")

#### 依赖监控（点击实例-》展示当前实例的依赖包信息）

![依赖包](https://images.gitee.com/uploads/images/2020/1209/152053_de25888f_1168339.png "屏幕截图.png")

#### Arthas命令操作

![输入图片说明](https://images.gitee.com/uploads/images/2020/1116/181250_4f502c7e_1168339.png "屏幕截图.png")
 
 ![输入图片说明](https://images.gitee.com/uploads/images/2020/0605/190447_b3cd9e91_1168339.png "屏幕截图.png")    


## 环境
- JDK 1.8
- MySQL 5.5+ 

## 功能

#### 已完成

| 功能       | 子功能         | 迭代版本 |
|----------|-------------|------|
| [远程主机命令下发（动态arthas）](docs/cn/arthas_tools.md) | arthas 命令兼容 | V1.2 |
|          |             |      |

#### 未完成


 | 功能      | 迭代版本 |
|---------|------|
| 线程栈监控   | V1.3 |
| 实时线程栈   | V1.3 |
| 实时线程图   | V1.3 |
| JVM基础参数 | V1.3 |
| 依赖包基础监控 | V1.3 |
|         |      |

 
## Q&A
- 因为目前自己抽时间在写，所以前端UI 有些小BUG ,功能、部署、脚本等等都在完善中，马上准备使用最新的VUE 那一套来进行页面的输出迭代了，欢迎各位大牛贡献代码。
- 欢迎大家各种star，fork，提issue，pull request，感觉还可以就点个star吧！
- 不能下载linux-tools 依赖的问题，可执行build 脚本，或执行下面的命令
- mvn install:install-file -Dfile=DependLib/linux-tools-1.8.jar -DgroupId=com.sun -DartifactId=linux-tools -Dversion=1.8 -Dpackaging=jar
#### 问题1
 No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK?

## 组织
 让我们一起学习成长，关注公众号获得每日一个知识点的储备，让我们一起成长


#### 微信关注

 ![输入图片说明](https://images.gitee.com/uploads/images/2020/1012/211345_e216e60c_1168339.jpeg "架构技术.jpg")


[![Giteye chart](https://chart.giteye.net/gitee/dromara/cubic/JQD5ZBUE.png)](https://giteye.net/chart/JQD5ZBUE)
