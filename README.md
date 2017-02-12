# DrCOM-Scut

Python版 scut drcom 认证  
本项目是Fork [seekwonderful/DrCOM-Scut](https://github.com/iseekwonderful/DrCOM-Scut) 
由于该项目最后更新是在16年8月份，在17年2月份无法正常使用，原因是新版客户端在一些认证包上增加了一些特征码，通过参考[scutclient/scutclient](https://github.com/scutclient/scutclient)
项目和通过`wireshark`抓包，补充这些特征码后使用。



## Getting Started

本程序支持安装有`python`及`python-codec`的环境下使用，包括但不限于Openwrt（本人未测试）、Padavan、Linux/Unix（本人未测试）等

#### Warning:
macOS 不支持 python 2.7 的raw socket，固无法使用

### Prerequisites

本程序依赖`python`及`python-codec`

本人使用的是newifi mini(MT7620, 128M RAM, 16M Flash)路由器，刷的是`padavan`固件
所以挂接U盘且安装了opt后，通过`opkg install python`安装python后即可正常使用

### Installing

#### 路由器使用

> python环境的安装，对于不同的固件，安装方式可能不同，具体的安装方式，请自行搜索

1. 安装`openwrt`或`Padavan`之类固件到路由器
2. 使用ssh登录上路由器
3. 更新openwrt包管理器: opkg update
4. 安装依赖项（具体安装情况可能不一样，
如Openwrt可通过在[openwrt downloads](https://downloads.openwrt.org/chaos_calmer/15.05.1/)
找到对应路由器cpu的型号的文件夹里面找到python的ipk包下载，然后上传（如scp、ftp）到路由器后安装
）: 
```
opkg install python
opkg install python-codec
```
5. 将本项目的`scutdrom.py`和`udp_auth.py`上传到路由器上
6. 运行: `python scutdrom.py -u username -p password -i interface` 
（其中`username`为你登录drcom使用的用户名，`password`为你登录drcom使用的用户名, `interface`为`WAN 口`对应的的网卡接口，, 一般情况下是`eth0`，对`OpenWRT`路由器一般为`eth0.2`, 对于`Padavan`为`eth2.2`,具体可以通过`ipconfig`命令查看）
7. 第6步执行的命令加入到路由器的开机自启动列表，具体自行搜索对应方式

#### Linux/Unix 使用（未测试）
1. 确保机器上安装有python
2. 通过`ipconfig`查看使用通信的网卡接口名称
3. 运行: `python scutdrom.py -u username -p password -i interface` 

## Authors

*Initial work* - [sheep/iseekwonderful](https://github.com/iseekwonderful)

*Fix* - [hexzhou](https://github.com/hexzhou)


## See Also

* [seekwonderful/DrCOM-Scut](https://github.com/iseekwonderful/DrCOM-Scut)
* [scutclient/scutclient](https://github.com/scutclient/scutclient)