# docker-demo
记录对demo的一些常用指令等
## 一、安装篇
  * 前提条件
   * Docker 运行在 CentOS 7 上，要求系统为64位、系统内核版本为 3.10 以上。
   * Docker 运行在 CentOS-6.5 或更高的版本的 CentOS 上，要求系统为64位、系统内核版本为 2.6.32-431 或者更高版本。

  * 查看centOS版本
   * uname -r

* 安装 Docker
  * yum -y install docker-io

* 查看docker指令帮助
 * docker help

* 查看docker版本
 * docker --version

## 二、操作篇
* 启动 Docker 后台服务
service docker start 

* 允许hello-world
docker run hello-world

* 查询远程官方仓库的centos镜像列
docker search centos

* 拉取官方镜像到本地
docker pull centos:7.0

* 根据dockerfile 创建一个新镜像（Dockerfile 是一个文本文件，包含了一条条的指令(Instruction)，每条指令都会构建一层）
docker build -t imageName:TAG . -f jdkdockerfile

* 复制文件进某容器中
docker cp test.jar containerID:/usr/local/

* 新建并启动一个容器，-t选项让Docker分配一个伪终端（pseudo-tty）并绑定到容器的标准输入上，
-i则让容器的标准输入保持打开。后台运行可使用-d参数，启动后会返回一个唯一id。
docker run -t -i -d imageName:TAG

* 查询容器的日志
docker container logs [container ID or NAMES]

* 启动已终止容器（状态为existed）
docker start [container ID or NAMES]

* 进入容器内部，操作容器
docker attach containerID

* 终止容器
docker container stop

* 在容器内部停止容器，等同exist
ctrl + d 

* 显示容器
docker container ls

* 删除容器
docker container rm containerID

## 三、Docker Hub
目前 Docker 官方维护了一个公共仓库 Docker Hub，其中已经包括了数量超过 15,000 的镜
像。大部分需求都可以通过在 Docker Hub 中直接下载镜像来实现。

* 拉取镜像仓库镜像
docker pull [选项] [Docker Registry 地址[:端口号]/]仓库名[:标签]

## 四、Docker三剑客，此处备注，留待学习
Docker Compose 
Docker Machine 
Docker Swarm 

## 五、底层实现
Docker 底层的核心技术包括 Linux 上的命名空间（Namespaces）、控制组（Control
groups）、Union 文件系统（Union file systems）和容器格式（Container format）。

## 六、CI/CD 持续集成/部署（GitHub  +  Drone ）
持续集成(Continuous integration)是一种软件开发实践，每次集成都通过自动化的构建（包括
编译，发布，自动化测试）来验证，从而尽早地发现集成错误。
持续部署（continuous deployment）是通过自动化的构建、测试和部署循环来快速交付高质
量的产品。与Jenkins不同的是，基于 Docker 的 CI/CD 每一步都运行在 Docker 镜像中，所以理论上
支持所有的编程语言。
