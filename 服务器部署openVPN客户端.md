# 服务器部署openVPN客户端

```text
 # 安装openssl和lzo，lzo用于压缩通讯数据加快传输速度
 sudo apt-get install openssl libssl-dev
 sudo apt-get install lzop
 # 安装openvpn和easy-rsa
 sudo apt-get install openvpn
 sudo apt-get install easy-rsa
```

**注意：如果是CentOS版本，用yum安装命令**

## CentOS安装报错

如果在安装时报错：

```cmd
CentOS Linux 8 - AppStream                       23  B/s |  38  B     00:01    
Error: Failed to download metadata for repo 'appstream': Cannot prepare internal mirrorlist: No URLs in mirrorlist
```

#### 原因

在2022年1月31日，CentOS团队终于从官方镜像中移除CentOS 8的所有包。

CentOS 8已于2021年12月31日寿终正寝，但软件包仍在官方镜像上保留了一段时间。现在他们被转移到[https://vault.centos.org](https://vault.centos.org/)

#### 解决方法：

如果你仍然需要运行你的旧CentOS 8，你可以在/etc/yum.repos中更新repos.d使用vault.centos.org代替mirror.centos.org

```cmd
#分别修改以下路径的文件中的内容
cd /etc/yum.repos.d
#分别打开对应文件
vi CentOS-Linux-BaseOS.repo
vi CentOS-Linux-AppStream.repo
vi CentOS-Linux-PowerTools.repo
```

CentOS-Linux-BaseOS.repo

```shell
[baseos]
name=CentOS Linux $releasever - BaseOS
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=BaseOS&infra=$infra
#baseurl=http://mirror.centos.org/$contentdir/$releasever/BaseOS/$basearch/os/
baseurl=https://vault.centos.org/centos/$releasever/BaseOS/$basearch/os/
gpgcheck=1
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial
```

CentOS-Linux-AppStream.repo

```shell
[appstream]
name=CentOS Linux $releasever - AppStream
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=AppStream&infra=$infra
#baseurl=http://mirror.centos.org/$contentdir/$releasever/AppStream/$basearch/os/
baseurl=https://vault.centos.org/centos/$releasever/AppStream/$basearch/os/ 
gpgcheck=1
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial
```

CentOS-Linux-PowerTools.repo

```shell
[baseos]
name=CentOS Linux $releasever - BaseOS
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=BaseOS&infra=$infra
#baseurl=http://mirror.centos.org/$contentdir/$releasever/BaseOS/$basearch/os/
baseurl=https://vault.centos.org/centos/$releasever/BaseOS/$basearch/os/
gpgcheck=1
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial
```

问题解决，CentOS也可以安装了

## 运行

将接收到的***.ovpn文件复制到 /etc/openvpn 中

启动命令：

```shell
openvpn /etc/openvpn/***.ovpn
```

#### 测试

```shell
telnet 172.25.47.87 8848
```

如出现：

![image-20220324101107764](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220324101107764.png)

表示连接成功



## 后台运行

1、在/etc/openvpn下目录下创建pempasswd文件并在其中写入openvpn密码：apoco01

2、将ca.art， ta.key证书和密钥复制到/etc/openvpn目录中

3、启动命令：

```shell
openvpn --daemon --cd /etc/openvpn/ --config /etc/openvpn/***.ovpn  --askpass /etc/openvpn/pempasswd --log-append /var/log/openvpn.log
```

4、查看是否后台启动

```shell
netstat -nap|grep openvpn
```

![image-20220324101930745](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220324101930745.png)

## 完成！