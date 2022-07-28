# Docker的安装


> 操作系统版本:Kali 2022.2

### 通过apt下载docker并启动docker服务
``` bash
sudo apt install -y docker.io
```

``` bash
sudo systemctl start docker
```

输入docker version查看docker的版本：

![版本](/images/Docker的安装/版本.jpg)

> 注意到这里只显示了Client的信息，下面有一个报错: persission denied
这是因为我们安装的时候是用的sudo安装，普通用户没有权限连接docker的服务端。
解决办法是把当前用户加入到docker组里面去。

### 添加当前用户到docker组并重启docker服务
``` bash
sudo groupadd docker
sudo gpasswd -a ${USER} docker
```

``` bash
sudo service docker restart
```
> 第一次实际操作时我不小心敲成restart docker了 

### 切换当前会话到docker组
``` bash
newgrp - docker
```

### 安装完成
再次输入docker version，正常显示完整信息：

![安装完成](/images/Docker的安装/成功.jpg)

### 后续步骤

#### Docker国内镜像加速
``` bash
sudo vim /etc/docker/daemonjson
```
添加：
``` json
{
    "registry-mirrors":[
        "https://vii0v3ojmirroraliyuncscom"
    ]
}
```

#### 设置开机启动Docker
``` bash
sudo systemctl enable docker
```

