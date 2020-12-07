
## 简介
  <a href='https://gitee.com/sanjiankethree/cubic/stargazers'><img src='https://gitee.com/sanjiankethree/cubic/badge/star.svg?theme=gvp' alt='star'></img></a>
  <a href='https://gitee.com/sanjiankethree/cubic/members'><img src='https://gitee.com/sanjiankethree/cubic/badge/fork.svg?theme=gvp' alt='fork'></img></a>
  
`Cubic` 是一个对应用透明，无侵入的java应用诊断工具，用于提升开发人员的诊断效率和能力。

`Cubic` 的目标是一站式java应用诊断解决方案，让开发人员无需登录机器或修改系统，就可以从日志、内存、线程、类信息、调试、机器和系统属性等各个方面对应用进行诊断，提升开发人员诊断问题的效率和能力。

`Cubic` 可调用内部自定义命令和动态加载arthas使用arthas 命令集。

因为很多公司使用监控需要进行定制化开发，Cubic 可作为一种技术参考，希望给大家带来些许启发。
 
技术体系：Spring Boot、Vue、Netty、Websocket、xterm等

 
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
6.  如使用IDEA 测试，在测试应用中加入配置 VM option 参数 如下：

```
-javaagent:/user/xxx/cubic-agent.jar  -Dcubic.agent.service_name=cubic-proxy
```
 

 ![应用列表](https://images.gitee.com/uploads/images/2020/1202/182824_706ae6ad_1168339.png "屏幕截图.png")

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

