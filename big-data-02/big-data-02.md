# 大数据-Day2:SSH免密码登录、集群搭建

**[HOME](../README.md)**

### **Hadoop主要组件：**

**Hadoop**：Java编写的软件框架，以支持数据密集型分布式应用

**ZooKeeper**：高可靠性分布式协调系统

**MapReduce**：针对大数据的灵活的并行数据处理框架

**HDFS**：Hadoop分布式文件系统

**Oozie**：负责MapReduce作业调度

**HBase**：Key-value数据库

**Hive**：构建在MapRudece之上的数据仓库软件包

**Pig**：Pig是架构在Hadoop之上的高级数据处理层。Pig Latin语言为编程人员提供了更直观的定制数据流的方法。



## SSH免密码登录：

**修改主机名：**sudo vim /etc/hostname

**设置虚拟机静态 ip：**sudo vim /etc/network/interfaces

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.xxx.128(129...)#每个虚拟机不一样，通常从128开始
netmask 255.255.255.0
network 192.168.xxx.0
boardcast 192.168.xxx.255
gateway 192.168.xxx.2#本地机器网关是1,与之区别用2

```

**配置 dns 服务器：**sudo vim /etc/resolv.conf

```
nameserver 8.8.8.8 8.8.4.4
```

**安装 ssh：** sudo apt-get install ssh

**生成公钥和私钥：**

```
cd ~
ssh-keygen -t rsa -P ''
cat  .ssh/id_rsa.pub  >>  .ssh/authorized_keys
ssh myhostname #测试登录自己
其他机子相同操作然后将公钥拷给master主机
scp  .ssh/id_rsa.pub   username@hostname:/home/username/id_rsa_1.pub
合并公钥
cat id_rsa_1.pub >> .ssh/authorized_keys
将合并后的公钥传给其他主机
scp .ssh/authorized_keys  username1@hostname1:/home/username1/.ssh/authorized_keys
```

