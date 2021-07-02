# Ubuntu安装 qbittorrent-nox并启动



### Qbittorrent-Nox

要在Linux上使用Qbittorrent Web UI，你无需安装完整的Qbittorent桌面应用程序，有一个基于终端的Qbittorrent应用程序可用，它被称为Qbittorrent-Nox。

注意：Web UI功能不仅限于Qbittorrent-Nox应用程序，此功能还可以与传统的Qbittorent Linux桌面应用程序一起使用



### 安装qbittorrent

#### 安装add-apt-repository命令
```bash
sudo apt-get update && sudo apt-get install software-properties-common -y
```
#### 添加qbittorrent-nox的PPA软件源
```bash
sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-stable
```
#### 安装qbittorrent-nox（webui版）
```bash
sudo apt-get update && sudo apt-get install qbittorrent-nox
```
### 设置开机启动
#### 通过rc.local完成

如果是Ubuntu-16.10及其之后的版本需要先按下面的文章完成设置后，开机启动才会生效

Ubuntu-18.04设置开机启动脚本
起因Ubuntu-16.10（不包括）之前的版本使用的是update-rc.d以及rc.local等方法设置开机启...

编辑rc.local脚本
```bash
nano /etc/rc.local
```
在exit 0前面（前一行）添加以下内容并保存
```bash
qbittorrent-nox -d
```
#### 通过创建自定义服务实现
创建系统服务
```bash
sudo apt-get install nano -y && nano /etc/systemd/system/qbittorrent-nox.service
```
粘贴以下内容，并保存。
```
[Unit]
Description=qBittorrent-nox
After=network.target

[Service]
User=root
Type=simple
RemainAfterExit=yes
ExecStart=/usr/bin/qbittorrent-nox -d

[Install]
WantedBy=multi-user.target
```

启动qbittorrent-nox并创建服务配置
```bash
systemctl start qbittorrent-nox
```
设置开机自动启动qbittorrent-nox
```bash
systemctl enable qbittorrent-nox
```

查看qbittorrent-nox状态
```bash
sudo systemctl status qbittorrent-nox
```

默认账号：admin 密码： adminadmin
默认登陆网址：ip:8080

