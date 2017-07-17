# 大数据-Day1:基础概念+Hadoop环境搭建

**[HOME](../README.md)**

## 基础概念：

### 1.结构化数据和非结构化数据

结构化数据也称作行数据，是由二维表结构来逻辑表达和实现的数据，严格地遵循数据格式与长度规范，主要通过关系型数据库进彳存储和管理。

非结构化数据是数据结构不规则或不完整，没有预定义的数据模型，不方便用数据库二维逻辑表来表现的数据。包括所有格式的办公文档、文本、图片、XML, HTML、各类报表、图像和音频/视频信息等等。

### 2.大数据是什么，有什么特点？

 大数据（big data），指无法在一定时间范围内用常规软件工具进行捕捉、管理和处理的数据集合，是需要新处理模式才能具有更强的决策力、洞察发现力和流程优化能力的海量、高增长率和多样化的信息资产。[1][ ]()

在[维克托·迈尔-舍恩伯格](https://baike.baidu.com/item/%E7%BB%B4%E5%85%8B%E6%89%98%C2%B7%E8%BF%88%E5%B0%94-%E8%88%8D%E6%81%A9%E4%BC%AF%E6%A0%BC)及肯尼斯·库克耶编写的《[大数据时代](https://baike.baidu.com/item/%E5%A4%A7%E6%95%B0%E6%8D%AE%E6%97%B6%E4%BB%A3/15434499)》[2][ ]() 中大数据指不用随机分析法（[抽样调查](https://baike.baidu.com/item/%E6%8A%BD%E6%A0%B7%E8%B0%83%E6%9F%A5)）这样捷径，而采用所有数据进行分析处理。大数据的5V特点（IBM提出）：Volume（大量）、Velocity（高速）、Variety（多样）、Value（低价值密度）、Veracity（真实性）。[3][ ]()

### 3.数据仓库

[数据仓库](https://baike.baidu.com/item/%E6%95%B0%E6%8D%AE%E4%BB%93%E5%BA%93)，英文名称为Data Warehouse，可简写为[DW](https://baike.baidu.com/item/DW/1264123)或DWH。数据仓库，是为[企业](https://baike.baidu.com/item/%E4%BC%81%E4%B8%9A)所有级别的决策制定过程，提供所有类型数据支持的战略[集合](https://baike.baidu.com/item/%E9%9B%86%E5%90%88)。它是单个数据存储，出于分析性报告和决策支持目的而创建。 为需要业务智能的企业，提供指导业务流程改进、监视时间、成本、质量以及控制。 

### 4.CAP理论

在[理论计算机科学](https://zh.wikipedia.org/wiki/%E7%90%86%E8%AB%96%E8%A8%88%E7%AE%97%E6%A9%9F%E7%A7%91%E5%AD%B8)中，**CAP定理**（CAP theorem），又被称作**布鲁尔定理**（Brewer's theorem），它指出对于一个[分布式计算系统](https://zh.wikipedia.org/wiki/%E5%88%86%E5%B8%83%E5%BC%8F%E8%AE%A1%E7%AE%97)来说，不可能同时满足以下三点：[[1\]](https://zh.wikipedia.org/wiki/CAP%E5%AE%9A%E7%90%86#cite_note-Lynch-1)[[2\]](https://zh.wikipedia.org/wiki/CAP%E5%AE%9A%E7%90%86#cite_note-2)

- [一致性](https://zh.wikipedia.org/wiki/%E4%B8%80%E8%87%B4%E6%80%A7)（Consistence) （等同于所有节点访问同一份最新的数据副本）
- 可用性（[Availability](https://zh.wikipedia.org/wiki/%E5%8F%AF%E7%94%A8%E6%80%A7)）（每次请求都能获取到非错的响应——但是不保证获取的数据为最新数据）
- 分区容错性（[Network partitioning](https://zh.wikipedia.org/w/index.php?title=Partition_tolerance&action=edit&redlink=1)）（以实际效果而言，分区相当于对通信的时限要求。系统如果不能在时限内达成数据一致性，就意味着发生了分区的情况，必须就当前操作在C和A之间做出选择[[3\]](https://zh.wikipedia.org/wiki/CAP%E5%AE%9A%E7%90%86#cite_note-3)。）

根据定理，分布式系统只能满足三项中的两项而不可能满足全部三项[[4\]](https://zh.wikipedia.org/wiki/CAP%E5%AE%9A%E7%90%86#cite_note-4)。理解CAP理论的最简单方式是想象两个节点分处分区两侧。允许至少一个节点更新状态会导致数据不一致，即丧失了C性质。如果为了保证数据一致性，将分区一侧的节点设置为不可用，那么又丧失了A性质。除非两个节点可以互相通信，才能既保证C又保证A，这又会导致丧失P性质。

## Ubuntu+Hadoop环境搭建

- vm安装ubuntu

  http://cdimage.ubuntu.com/releases/14.04/release/

- 下载vim,openssh-server,lrzsz

  ```
  ~$ sudo apt-get install vim openssh-server lrzsz
  ```

- 查看ip地址，Xshell远程登录

  ```
  ~$ ifconfig
  ```

- 添加root用户密码

  ```c
  ~$ sudo passwd root
  ```

- 添加用户

  ```
  ~$ su
  ~$ adduser hadoop
  ~$ su hadoop
  ```



- 安装jdk

  http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html

  ```
  ~$ wget 
  ~$ cd ~
  ~$ mkdir software
  ~$ rz
  ~$ tar -zxvf jdk-7u80-linux-x64.tar.gz
  ~$ mv jdk1.7.0_80 jdk1.7
  ~$ vim ~/.bashrc //全局变量修改 /etc/profile.d/xx.sh
  #结尾添加
  export JAVA_HOME=/home/hadoop/software/jdk1.7
  export PATH=$PATH:$JAVA_HOME/bin
  ~$ source ~/.bashrc
  ~$ java -version
  ```

- 安装hadoop

  ```
  ~$ wget http://mirrors.tuna.tsinghua.edu.cn/apache/hadoop/common/hadoop-2.6.0/hadoop-2.6.0.tar.gz
  ~$ tar -zxvf hadoop-2.6.0.tar.gz
  ~$ vim ~/.bashrc
  #结尾添加
  export HADOOP_HOME=/home/hadoop/software/hadoop-2.6.0
  export PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin
  export CLASSPATH=.:$CLASSPATH:$HADOOP_HOME/share/hadoop/common/hadoop-common-2.6.0.jar:$HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-client-core-2.6.0.jar:$HADOOP_HOME/share/hadoop/common/lib/commons-cli-1.2.jar
  ~$ source ~/.bashrc
  ~$ hadoop version
  ```

  ​