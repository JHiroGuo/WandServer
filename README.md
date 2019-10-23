# WandServer

[中文](#简介)

#### About

WandServer is an open source software developed by Beijing tiretime technology co., LTD.(www.tiertime.com), which controls tiretime 3D printer. Customers can design and develop their own App according to their own needs, and control 3D printer to print and monitor 3D model files through the open source interface.

#### Usage

Download link：

window：https://pan.baidu.com/s/11DgXSKNbfmEQcUCQz94Rbg&shfl=sharepset   pwd: s6zn

macOS:    https://pan.baidu.com/s/1NSVd-l7-IjB-B8Z32LWGfg&shfl=sharepset           pwd: 7h3u

linux：	https://pan.baidu.com/s/1VlAwHMjhuNHPdX1HL4m2zw                                pwd: tmdb



Download the corresponding system platform program (Window, Linux or macOS), unzip it and enter the folder. Double-click to start WandServer. Or go to the terminal

```python
./WanderServer
```

 to start. WandServer USES port 3333 by default.

The client can send the corresponding instruction to the host 3333 interface of WandServer through websock to control the printer.

⚠️⚠️⚠️ When the Linux system starts up WandServer for the first time, it needs to copy tiertime.rules from the downloaded package to the system ` /etc/udev/rules.d/` path under the terminal, otherwise the USB link printer cannot be used.

```python
sudo cp tiertime.rules /etc/udev/rules.d/
```

#### API Guide

[ English ](API_en.md)

[ 中文 ](API_zh.md)

#### Client

##### JaveScript

eg：Search net printer cmd

```js
var socket = new WebSocket("ws://127.0.0.1:3333");

function searchnetprinter(){
	var obj = {};
	obj["cmd"]= "searchnet";
	
	var cmd = JSON.stringify( object );
	socket.send(cmd);
}
```

Index.html  is a simple html socket example, can be a simple reference.





[English](#About)

#### 简介

WandServer 是北京市太尔时代科技有限公司研发的一款，控制太尔时代3D打印机的开源软件。客户可以根据自己的需求设计开发自己的App，并通过开源的接口，控制3D打印机进行3D模型文件打印和监控。

#### 使用

下载链接：

window：https://pan.baidu.com/s/11DgXSKNbfmEQcUCQz94Rbg&shfl=sharepset   pwd: s6zn

macOS:    https://pan.baidu.com/s/1NSVd-l7-IjB-B8Z32LWGfg&shfl=sharepset           pwd: 7h3u

linux：	https://pan.baidu.com/s/1VlAwHMjhuNHPdX1HL4m2zw                                pwd: tmdb



下载对应平台 Window、Linux或者macOS的程序，解压后进入该文件夹。双击启动WandServer。或者进入终端 

```
./WanderServer
```

 启动。WandServer默认使用3333端口通讯。

客户可以通过 sock 向Wand Server运行程序的主机3333接口，发送对应的指令，完成控制打印机。

⚠️⚠️⚠️  Linux 系统下第一次启动WandServer 需要在终端下 将下载的压缩包内的 tiertime.rules 拷贝到 系统 `/etc/udev/rules.d/` 路径下，否则USB链接打印机无法使用。

```python
sudo cp tiertime.rules /etc/udev/rules.d/
```



#### 接口文档说明

[ English ](API_en.md)

[ 中文 ](API_zh.md)

#### 客户端

##### JaveScript

例如：获取网络打印机

```js
var socket = new WebSocket("ws://127.0.0.1:3333");

function searchnetprinter(){
	var obj = {};
	obj["cmd"]= "searchnet";
	
	var cmd = JSON.stringify( object );
	socket.send(cmd);
}
```



index.html 是一个简单的Html socket 例子，可以简单参考。



