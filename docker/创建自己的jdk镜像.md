### 创建dockerFile

```sh
FROM centos:7
MAINTAINER  jameswang@
ADD jdk-8u144-linux-x64.tar.gz /usr/local/
ENV JAVA_HOME /usr/local/jdk1.8.0_144
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV PATH $PATH:$JAVA_HOME/bin
```
### 使用Dockerfile创建镜像

```sh
sudo docker build -t jdk-8u192:latest . -f Dockerfile
```

### 给你要上传的镜像打个tag

```sh
docker tag [source_name] xxx.xxx.xx.xx:8082/[target_name]:latest
```

### push 

```sh
sudo  docker push xxx.xxx.xx.xx:8082/jdk-8u192
```

### search私服中中镜像

```sh
docker search xxx.xxx.xx.xx:8082/jdk-8u192
```

### pull 私服中的镜像

```sh
sudo  docker pull  xxx.xxx.xx.xx:8082/jdk-8u192
```

### docker 中添加host

```sh
--hostname ：指定hostname;
--net : 指定网络模式
--ip：指定IP
--add-host ：指定往/etc/hosts添加的host
```
- example

```
docker run -itd --name hadoop0 --hostname hadoop0 --net network_my --ip 192.168.10.30 --add-host hadoop1:192.168.10.31 --add-host hadoop2:192.168.10.32  -d -P -p 50070:50070 -p 8088:8088 hadoop:master
```
---------------------
作者：淡淡的倔强 
来源：CSDN 
原文：https://blog.csdn.net/u012834750/article/details/80508464?utm_source=copy 
版权声明：本文为博主原创文章，转载请附上博文链接！


###  Maven 插件之 docker-maven-plugin 的使用
- [Maven 插件之 docker-maven-plugin 的使用](https://blog.csdn.net/aixiaoyang168/article/details/77453974)

### maven 项目和nuex整合
- [整合内容](https://github.com/jameswangAugmentum/Blogs/issues/2)

- mvn clean package docker:build 只执行 build 操作
- mvn clean package docker:build -DpushImage 执行 build 完成后 push 镜像
- mvn clean package docker:build -DpushImageTag 执行 build 并 push 指定 tag 的镜像
- 注意：这里必须指定至少一个 imageTag，它可以配置到 POM 中，也可以在命令行指定。命令行指定如下：mvn clean package docker:build -DpushImageTags DdockerImageTags=imageTag_1 -DdockerImageTags=imageTag_2

### 给mongo添加用户密码校验
## 进入目录
use dbname 
## 创建用户
db.createUser({user:"cas-ticket", pwd:"111111", roles:[{role:"readWrite", db: "cas"}]})




