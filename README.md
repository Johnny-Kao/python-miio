# 小米智能家居接入终端

## 用途

从MAC OS Terminal下指令，操作小米扫地机器人（Xiaomi Mi Robot Vacuum）、小米智能开关（Xiaomi Mi Smart WiFi Socket）等智能家居设备

## 简易流程

1. 提取智能家居设备的IP、TOKEN
2. 安装必要的套件
3. 优化指令

## 使用软件

1. [网易MuMu虚拟机](https://mumu.163.com/) - 用于模拟安卓环境，并提取家居设备的TOKEN
2. [米家APP 5.4.54 版本](https://github.com/Johnny-Kao/python-miio/blob/master/Mi%20Home_v5.4.5.apk) - 用于提取家居设备的TOKEN
3. [Rytilahti/python-miio](https://github.com/rytilahti/python-miio) - 操作指令

## 具体使用方式

1. 下载网易MuMu虚拟机后，并安装米家APP 5.4.54 版本APK，具体的操作细节，可从网易MuMu的官方网站查询。
2. 登录米家APP，把所有的智能设备都打开后关闭，让APP缓存所有设备的资讯。
3. 使用安卓自带的文件管理器进入/sdcard/SmartHome/logs/Plug_Devicemanager/，里面有一个yyyy-mm-dd.txt
4. 文件中有所有设备的IP地址、TOKEN，记下来备用
	* 备注：重置网络设备后，会影响IP、TOKEN，需要重新获取
5. 打开终端机，执行下列指令

	* 以Python3安装套件
	
	```
	pip3 install python-miio
	```
	
	* 安装成功后，把第4步骤的IP、TOKEN拿来使用，以打开小米智能插座为例
	
	```
	miplug --ip 192.168.xxx.xxx --token xxxxxxxx on'
	```
	
	* 执行完毕后，你会发现插座已经打开了，其他操作的指令可以参考：[智能设备操作智能](https://python-miio.readthedocs.io/en/latest/)

6. 进行优化输入方式，加入优化指令进~/.zshrc文件
	* 把IP、TOKEN都缩短成指令lamp，之后可以输入lamp on打开设备、lamp off关闭设备、lamp status查询设备状态
	
	```
	alias lamp='miplug --ip 192.168.xxx.xxx --token xxxxxxxx'
	```
7. 重新更新系统文件

```
source ~/.zshrc
```

	