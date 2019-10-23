# 服务器程序接口说明

## 打印机指令接口

<table>
  <tr>
    <th>Version</th>
    <th> Data</th>
    <th> Author </th>
    <th> Note</th>
  </tr>
  <tr>
    <td>V0.0.1</td>
    <td>2019-2-18</td>
    <td>GJH</td>
    <td>打印机指令</td>
  </tr>
  <tr>
      <td>...</td>
      <td>2018-2-20</td>
      <td>GJH</td>
      <td>新增耗时操作流程</td>
  </tr>
  <tr>
      <td>...</td>
      <td>2019-7-4</td>
      <td>GJH</td>
      <td>新增打印流程以及打印控制流程</td>
  </tr>
  <tr>
    <td>V0.1.0</td>
    <td>2019-9-30</td>
    <td>GJH</td>
    <td>新增WandServer接口</td>
  </tr>
  <tr>
    <td>....</td>
    <td>2019-10-09</td>
    <td>GJH</td>
    <td>新增链接打印机接口</td>
  </tr>
  <tr>
    <td>...</td>
    <td>2019-10-15</td>
    <td>GJH</td>
    <td>新增打印机控制指令</td>
  </tr>
</table>


```
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    -- i5ting_toc -f ReadMe.md -o           
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
```



### 搜索USB链接

只用于服务器端搜索链接的USB打印机，不进行结果返回。

`{"cmd":"searchusb"} `

返回数据

```json
{
  "receipted": {
    "cmd": "searchusb"
  },
  "reply": {
    "status": 0,
    "message": "Success"
  }
}
```

### 查询服务器端USB设备

只返回服务器端已经查询到的USB设备，不进行USB设备搜索。

`{"cmd":"usbdevlist"}`

返回结果：

```json
{
	"receipted":{
		"cmd":"usbdevlist"
	},
	"reply":{
		"status":0,
		"message":"Success",
		"result": [
            {
                "printName": "260029",
                "serNum": 260029
            }
        ]
	}
}
```

### 搜索网络打印机

只用于搜索网络打印机，不进行结果返回。

`{"cmd":"searchnet"}`

返回结果：

```json
{
	"recipted":{
		"cmd":"searchnet"
	},
	"reply":{
		"status":0,
		"message":"Success"
	}
}
```

### 查询服务器端网络打印机设备

该命令只用于查询服务器端已经查询到的网络打印机设备，不进行网络设备搜索。

`{"cmd":"netdevlist"}`

返回结果：

```json
{
	"recipted":{
		"cmd":"netdevlist"
	},
	"reply":{
		"status":0,
		"message":"Success",
		"result": [
            {
                "accessCtrl": 0,
                "haveHost": 0,
                "hostName": "",
                "ipAddr": "192.168.7.104",
                "printName": "260029",
                "printType": "Mini2 (NTC)",
                "serNum": 260029,
                "systemType": 10112
            }
        ]
	}
}
```

### 查询在线打印机（USB+NetWork）

该指令用户查询服务器端所有的在线的打印机，只用于结果返回。

`{"cmd":"searchall"}`

返回结果：

```json
{
	"recipted":{
		"mcd":"searchall"
	},
	"reply":{
		"status":0,
		"message":"Success",
		"result":{
            "net": [
                {
                    "accessCtrl": 0,
                    "haveHost": 0,
                    "hostName": "",
                    "ipAddr": "192.168.7.104",
                    "printName": "260029",
                    "printType": "Mini2 (NTC)",
                    "serNum": 260029,
                    "systemType": 10112
                }
            ],
            "usb": [
                {
                    "printName": "260029",
                    "serNum": 260029
                }
            ]
        }
	}
}
```

### 链接USB打印机

该指令用于，客户端链接服务端在线的USB打印机。

`{"cmd":"usbconnect,"sn":"260029"}`

返回结果

```json
{
	"recipted":{
		"mcd":"usbconnect",
    "sn":"260029"
	},
	"reply":{
		"status":0,
		"message":"Success"
	}
}
```



### 链接Net打印机

该指令用于，客户端链接服务端在线的网络打印机。

` {"cmd":"netconnect","sn":"260029"}`

返回结果

```json
{
    "receipted": {
        "cmd": "netconnect",
        "sn": "260029"
    },
    "reply": {
        "status": 0,
      	"message":"SUCCESS"
    }
}
```



### 断开链接

该指令用于，客户端断开服务器端已连接的打印机。

` {"cmd":"disconnect","sn":"260029"}`

返回结果

```json
{
    "receipted": {
        "cmd": "disconnect",
        "sn": "260029"
    },
    "reply": {
        "status": 0,
        "message":"SUCCESS"
    }
}
```

### 获取打印机状态

该指令用于，客户端获取服务器端已经链接的打印机状态。

`{"cmd":"getprintstatus","sn":"260029"}`

返回结果

```json
{
    "receipted": {
        "cmd": "getprintstatus",
        "sn": "260029"
    },
    "reply": {
        "result": {
            "basePlatTemp": 38.1,
            "curHeight": 0,
            "curLayer": 0,
            "heaterOn": 0,
            "inPort_Slave": 0,
            "intPort": 7863,
            "motorPositionW": 2000,
            "motorPositionX": -100,
            "motorPositionY": 30,
            "motorPositionZ": -70,
            "motorStatusW": 40,
            "motorStatusX": 0,
            "motorStatusY": 0,
            "motorStatusZ": 0,
            "nozzleTemp1": 61.46,
            "nozzleTemp2": 241.98000000000002,
            "outPort": 83329,
            "outPort_Slave": 0,
            "printerStatus": 1,
            "remainRercent": 0,
            "remainTime": 0,
            "reserved1": -4,
            "reserved2": -1,
            "systemStatus": 3
        },
        "status": 0
    }
}
```



### 初始化打印机

该指令用于，控制服务器端已经链接的打印机进行初始化。

`{"cmd":"exec","sn":"260029","action":"initprinter"}`

返回结果

```json
{
    "receipted": {
        "action": "initprinter",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49867",
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "initprinter",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49867",
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}

```

### 获取正在打印的任务名称

该指令用于获取正在打印的任务名称

`{"cmd":"exec","sn":"260029","action":"jobcurrent"}`

返回结果

```json
 {
    "receipted": {
        "action": "jobcurrent",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50186",
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "jobcurrent",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50186",
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "result": {
            "jobname": "cube.tsk"
        },
        "status": 0
    }
}
```



### 暂停打印

该指令用于，客户端暂停服务端在线并且正在打印的打印机。

`{"cmd":"exec","sn":"260029","action":"pauseprint"}`

返回结果

```json
 // 服务器端 接收指令成功
 {
        "action": "pauseprint",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49851",
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

// 执行指令 成功
{
    "receipted": {
        "action": "pauseprint",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49851",
        "sn": "260029"
    },
    "reply": {
        "message": "SUCCESS.",
        "status": 0
    }
}

```



### 恢复打印

该指令用于，控制服务器端已经暂停的打印机，恢复打印工作。

`{"cmd":"exec","sn":"260029","action":"resumeprint"}`

返回结果

```json
{
    "receipted": {
        "action": "resumeprint",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49851",
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "resumeprint",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49851",
        "sn": "260029"
    },
    "reply": {
        "message": "SUCCESS.",
        "status": 0
    }
}

```

### 停止打印

该指令用于，停止服务器端正在进行打印工作的打印机。

`{"cmd":"exec","sn":"260029","action":"stopprint"}`

返回结果

```json
{
    "receipted": {
        "action": "stopprint",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49851",
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "stopprint",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49851",
        "sn": "260029"
    },
    "reply": {
        "message": "SUCCESS.",
        "status": 0
    }
}

```

### 自动对高

该命令用于控制打印机进行自动对高

`{"cmd":"exec","sn":"260029","action":"autoheight"}`

返回结果

```json
{
    "receipted": {
        "action": "autoheight",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49851",
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "autoheight",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49851",
        "sn": "260029"
    },
    "reply": {
        "message": "SUCCESS.",
        "status": 0
    }
}
```

### 自动校准

该指令用于打印机平台自动校准

`{"cmd":"exec","sn":"260029","action":"autoplat"}`

返回结果

```json
{
    "receipted": {
        "action": "autoplat",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49851",
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "autoplat",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49851",
        "sn": "260029"
    },
    "reply": {
        "message": "SUCCESS.",
        "status": 0
    }
}
```



### 获取历史列表

该指令用于获取，已经链接的打印机的历史列表

`{"cmd":"exec","sn":"260029","action":"historylist"}`

返回结果

```json
{
    "receipted": {
        "action": "historylist",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50171",
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "historylist",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50171",
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "result": [
            {
                "date": "---",
                "hostname": "gjh",
                "jobstatus": 3,
                "printtimes": 726,
                "taskid": 1,
                "taskname": "prism.tsk"
            }
        ],
        "status": 0
    }
}
```



### 获取打印列表

该指令用于获取打印列表

`{"cmd":"exec","sn":"260029","action":"joblist"}`

返回结果

```json
 {
    "receipted": {
        "action": "joblist",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50171",
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "joblist",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50171",
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "result": {
            "currentjob": "2",
            "list": [
                {
                    "date": "2019-10-14 17:03:22",
                    "hostname": "Unknow",
                    "jobid": 13,
                    "jobstatus": 0,
                    "printtimes": 81826,
                    "taskid_list": [
                        17,
                        18
                    ],
                    "taskname_list": [
                        "cube.tsk",
                        "独角羊.tsk"
                    ],
                    "weight": 521.165142
                },
                {
                    "date": "2019-10-14 17:14:27",
                    "hostname": "Unknow",
                    "jobid": 14,
                    "jobstatus": 0,
                    "printtimes": 81826,
                    "taskid_list": [
                        19,
                        20
                    ],
                    "taskname_list": [
                        "cube.tsk",
                        "独角羊.tsk"
                    ],
                    "weight": 521.165142
                },
                {
                    "date": "2019-10-15 09:19:47",
                    "hostname": "Unknow",
                    "jobid": 16,
                    "jobstatus": 0,
                    "printtimes": 81826,
                    "taskid_list": [
                        21,
                        22
                    ],
                    "taskname_list": [
                        "cube.tsk",
                        "独角羊.tsk"
                    ],
                    "weight": 521.165142
                }
            ],
            "printerStatus": "1"
        },
        "status": 0
    }
}

```

### 删除打印任务

该指令用于删除打印列表中的打印任务。注意：参数中type 0为打印列表 1为历史列表

`{"cmd":"exec","sn":"260029","action":"jobdelete","jobid":16,"type":0}`

返回结果

```json
 {
    "receipted": {
        "action": "jobdelete",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50180",
        "jobid": 14,
      	"type":0,
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "jobdelete",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50180",
        "jobid": 14,
      	"type":0,
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}
```

### 移动打印任务位置

该指令用于，上下移动打印任务的位置

`{"cmd":"exec","sn":"260029","action":"adjustjob","jobid":12,"down":true}`

返回结果

```json
{
    "receipted": {
        "action": "adjustjob",
        "cmd": "exec",
        "down": true,
        "ipPort": "::ffff:127.0.0.1-50186",
        "jobid": 10,
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "adjustjob",
        "cmd": "exec",
        "down": true,
        "ipPort": "::ffff:127.0.0.1-50186",
        "jobid": 10,
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}
```

### 上传文件到服务器

该指令用于客户端，上传本地文件到服务器。注意：指令中的data对应的为 文件的二进制内容。

`{"cmd":"uploadfile","filename":"cube.tsk","data":"........"}`

返回结果

```json
 {
    "receipted": {
        "cmd": "uploadfile",
        "filename": "cube.tsk",
        "ipPort": "::ffff:127.0.0.1-50230"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}

{
    "receipted": {
        "cmd": "uploadfile",
        "filename": "cube.tsk",
        "ipPort": "::ffff:127.0.0.1-50230"
    },
    "reply": {
        "message": "Success.",
        "result": {
            "filepath": "/var/folders/g8/z8kmspv509gbw48_8wtzp7sw0000gn/T/cube.tsk"
        },
        "status": 0
    }
}
```

### 将打印任务发给打印机

该指令用于将已经上传到服务器端的打印任务，发送给打印机。

```json
{
	"cmd": "exec",
	"sn": "260029",
	"action": "sendtaskfile",
	"filepaths": ["/var/folders/g8/z8kmspv509gbw48_8wtzp7sw0000gn/T/cube.tsk"],
	"username": "gjh_web"
}
```

返回结果

```json
{
    "receipted": {
        "action": "sendtaskfile",
        "cmd": "exec",
        "filepaths": [
            "/var/folders/g8/z8kmspv509gbw48_8wtzp7sw0000gn/T/cube.tsk"
        ],
        "ipPort": "::ffff:127.0.0.1-50230",
        "sn": "260029",
        "username": "gjh_web"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "sendtaskfile",
        "cmd": "exec",
        "filepaths": [
            "/var/folders/g8/z8kmspv509gbw48_8wtzp7sw0000gn/T/cube.tsk"
        ],
        "ipPort": "::ffff:127.0.0.1-50230",
        "sn": "260029",
        "username": "gjh_web"
    },
    "reply": {
        "message": "File is sending. ",
        "result": {
            "nprogress": 7,
            "strprogress": "\nSending task files --- 7.1 %"
        },
        "status": 3
    }
}

	.....
	
{
    "receipted": {
        "action": "sendtaskfile",
        "cmd": "exec",
        "filepaths": [
            "/var/folders/g8/z8kmspv509gbw48_8wtzp7sw0000gn/T/cube.tsk"
        ],
        "ipPort": "::ffff:127.0.0.1-50230",
        "sn": "260029",
        "username": "gjh_web"
    },
    "reply": {
        "message": "File is sending. ",
        "result": {
            "nprogress": 100,
            "strprogress": "Send tsk file success."
        },
        "status": 3
    }
}

{
    "receipted": {
        "action": "sendtaskfile",
        "cmd": "exec",
        "filepaths": [
            "/var/folders/g8/z8kmspv509gbw48_8wtzp7sw0000gn/T/cube.tsk"
        ],
        "ipPort": "::ffff:127.0.0.1-50230",
        "sn": "260029",
        "username": "gjh_web"
    },
    "reply": {
        "message": "Success.",
        "result": {
            "jobid": 19
        },
        "status": 0
    }
}

```

### 检查任务是否可以打印

该指令用于检测，打印任务是否可以打印。包括 材料、机型以及喷头等

`{"cmd":"exec","sn":"260029","action":"jobcanprepare","jobid":3}`

返回结果

```json
{
    "receipted": {
        "action": "jobcanprepare",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50305",
        "jobid": 3,
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "jobcanprepare",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50305",
        "jobid": 3,
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}
```



### 启动任务准备

该指令用于在检查打印任务可以打印后，启动打印任务数据准备工作。

`{"cmd":"exec","sn":"260029","action":"jobprepare","jobid":3}`

返回结果

```json
 {
    "receipted": {
        "action": "jobprepare",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50305",
        "jobid": 3,
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "jobprepare",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50305",
        "jobid": 3,
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}
```



### 启动打印任务

该指令用于在数据准备之后，启动该打印任务。

`{"cmd":"exec","sn":"260029","action":"jobprint","jobid":3}`

返回i结果

```json
 {
    "receipted": {
        "action": "jobprint",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50305",
        "jobid": 3,
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "jobprint",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50305",
        "jobid": 3,
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}

```



### 直接启动打印任务

该指令用于直接启动打印任务，内部包括流程: 任务检测------>数据准备------>启动打印

`{"cmd":"exec","sn":"260029","action":"jobprepareprint","jobid":3}`

返回结果

```json
 {
    "receipted": {
        "action": "jobprepareprint",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50305",
        "jobid": 3,
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "jobprepareprint",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50305",
        "jobid": 3,
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}
```



### 打印本地任务的流程

客户端想要实现打印本地任务，必须经过以下流程：

将本地打印任务上传到服务器------>将已经到服务器的任务发送给打印机------>直接启动已经上传到打印机的任务



### 获得所支持的材料信息

该指令用于获取打印机内部保存的所有的材料信息。

`{"cmd":"exec","sn":"260029","action":"getmaterials"}`

返回结果

```json
{
    "receipted": {
        "action": "getmaterials",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50433",
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "result": [
            {
                "color": 0,
                "density": 1.0499999523162842,
                "name": "ABS",
                "plattemp": 90,
                "sendscale": 10,
                "shrinkscale_x": 1.0000000656873453e-05,
                "shrinkscale_y": 1.0000000656873453e-05,
                "shrinkscale_z": 1.0000000656873453e-05,
                "temperatur": 270,
                "type": 65556
            },
            {
                "color": 0,
                "density": 1.0499999523162842,
                "name": "ABS+",
                "plattemp": 90,
                "sendscale": 10,
                "shrinkscale_x": 1.0000000656873453e-05,
                "shrinkscale_y": 1.0000000656873453e-05,
                "shrinkscale_z": 1.0000000656873453e-05,
                "temperatur": 274,
                "type": 65553
            },
            {
                "color": 0,
                "density": 1.25,
                "name": "PLA",
                "plattemp": 50,
                "sendscale": 10,
                "shrinkscale_x": 1.0000000656873453e-05,
                "shrinkscale_y": 1.0000000656873453e-05,
                "shrinkscale_z": 1.0000000656873453e-05,
                "temperatur": 210,
                "type": 66024
            },
            {
                "color": 0,
                "density": 1.2100000381469727,
                "name": "TPU",
                "plattemp": 40,
                "sendscale": 10,
                "shrinkscale_x": 1.0000000656873453e-05,
                "shrinkscale_y": 1.0000000656873453e-05,
                "shrinkscale_z": 1.0000000656873453e-05,
                "temperatur": 230,
                "type": 66286
            },
            {
                "color": 0,
                "density": 1.0499999523162842,
                "name": "是是是",
                "plattemp": 90,
                "sendscale": 10,
                "shrinkscale_x": 9.999999747378752e-06,
                "shrinkscale_y": 9.999999747378752e-06,
                "shrinkscale_z": 9.999999747378752e-06,
                "temperatur": 270,
                "type": 1962917546
            }
        ],
        "status": 0
    }
}

```



### 获取当前材料信息

该指令用于获取当前设置材料的详细信息。

`{"cmd":"exec","sn":"260029","action":"getcurmaterial"}`

返回信息

```json
 {
    "receipted": {
        "action": "getcurmaterial",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50433",
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "getcurmaterial",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50433",
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "result": {
            "color": 0,
            "density": 1.0499999523162842,
            "name": "ABS+",
            "plattemp": 90,
            "sendscale": 10,
            "shrinkscale_x": 1.0000000656873453e-05,
            "shrinkscale_y": 1.0000000656873453e-05,
            "shrinkscale_z": 1.0000000656873453e-05,
            "temperatur": 274,
            "type": 65553
        },
        "status": 0
    }
}
```



### 设置打印机材料

该指令用于设置打印机材料，其中参数matid 为材料详情里面的type ,weight的单位为克

`{"cmd":"exec","sn":"260029","action":"getcurmaterial","matid":66286,"weight":999}`

返回结果

```json
{
    "receipted": {
        "action": "savematerial",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50516",
        "matid": 66286,
        "sn": "260029",
        "weight": 999
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "savematerial",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50516",
        "matid": 66286,
        "sn": "260029",
        "weight": 999
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}
```



### 重置打印机SD卡

该指令用于重置打印机SD卡，包括语言和材料等。

`{"cmd":"exec","sn":"260029","action":"resetsdcard"}`

返回结果

```
 {
    "receipted": {
        "action": "resetsdcard",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50529",
        "sn": "260029"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "resetsdcard",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50529",
        "sn": "260029"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}
```















### X5 机型底板复位

该命令适用于X5 打印机，重置底板。

`{"cmd":"exec","sn":"450899","action":"resetplat"}`

返回结果

```json
 {
    "receipted": {
        "action": "resetplat",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49867",
        "sn": "450899"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "resetplat",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49867",
        "sn": "450899"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}

```

### X5 机型更换底板

该命令适用于X5 打印机，更换底板。

`{"cmd":"exec","sn":"450899","action":"platechange"}`

返回结果

```json
 {
    "receipted": {
        "action": "platechange",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49867",
        "sn": "450899"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "platechange",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49867",
        "sn": "450899"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}

```

### X5 机型侧门开关

该命令适用于X5 打印机，侧门开关。

`{"cmd":"exec","sn":"450899","action":"sidedooropen"}`

返回结果

```json
 {
    "receipted": {
        "action": "sidedooropen",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49867",
        "sn": "450899"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "sidedooropen",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-49867",
        "sn": "450899"
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}

```

### X5 设置自动打印

该命令适用于X5 打印机，设置或者读取是否连续打印。		

读取连续打印标识 `{"cmd":"exec","sn":"450899","action":"autoprintflag"}`	

设置连续打印标识 `{"cmd":"exec","sn":"450899","action":"autoprintflag","set":1,"value":1}`

返回结果

```json
// 读取标示
{
        "action": "autoprintflag",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50148",
        "sn": "450899"
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "autoprintflag",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50148",
        "sn": "450899"
    },
    "reply": {
        "message": "Success.",
        "result": {
            "autoreplace": "1"
        },
        "status": 0
    }
}

// 设置标识
 {
    "receipted": {
        "action": "autoprintflag",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50148",
        "set": 1,
        "sn": "450899",
        "value": 0
    },
    "reply": {
        "message": "Server Receive Success. ",
        "status": 2
    }
}

{
    "receipted": {
        "action": "autoprintflag",
        "cmd": "exec",
        "ipPort": "::ffff:127.0.0.1-50148",
        "set": 1,
        "sn": "450899",
        "value": 0
    },
    "reply": {
        "message": "Success.",
        "status": 0
    }
}
		
```

















### ～～～～～～👇老接口～～～～～

### 搜索打印机

客户端链接上服务器端程序之后，在未知服务器端所链接的打印机情况下。首先需要搜索服务器所能搜索到的打印机。客户端需要发送的`json`指令：

` { "nCmd": 1 }` 	

服务器端搜索完打印机之后，返回的搜索到的打印机数据格式如下：

```json
{
    "result":{
        "list":{
            "linked":[
                {
                    "bAfinia":false,
                    "bBeConnect":false,
                    "bHaveHost":true,
                    "bHavePassword":false,
                    "bNewMode":true,
                    "bOnLine":true,
                    "nType":10112,
                    "strIP":"192.168.6.139",
                    "strName":"2",
                    "strSN":"260029"
                }
            ],
            "ulink":[
                {
                    "bAfinia":false,
                    "bBeConnect":false,
                    "bHaveHost":true,
                    "bHavePassword":false,
                    "bNewMode":true,
                    "bOnLine":true,
                    "nType":10115,
                    "strIP":"192.168.6.112",
                    "strName":"U",
                    "strSN":"551071"
                },
                {
                    "bAfinia":false,
                    "bBeConnect":false,
                    "bHaveHost":true,
                    "bHavePassword":false,
                    "bNewMode":true,
                    "bOnLine":true,
                    "nType":10115,
                    "strIP":"192.168.6.124",
                    "strName":"U",
                    "strSN":"551069"
                }
            ]
        },
        "message":"Success.",
        "nCmd":1,
        "status":0
    }
}
```
其中 `ulink` 代表服务器端为未链接的打印机，`linked`代表已经链接了的打印，则客户端直接可以对已经的链接的打印机发送相应的指令。

### 链接打印机
`json`指令：

``` json
 {
     "nCmd": 2,
     "strSN": "260029",
     "args": 
     {
         "pwd": "888888"
     }
 }

```
返回的`json`数据

```json
{
    "result":{
        "message":"Success.",
        "nCmd":2,
        "status":0
    }
}
```


### 重置打印机

`json`指令：

```json
{
        "nCmd": 15,
        "strSN": "260029"
}
```

返回的`json`数据

```json
{
    "result":{
        "strSN":"260029",
        "nCmd":15,
        "status":0,
        "message":"Success."
    }
}
```



### 自动对高(耗时操作)

`json`指令：

```json
{
        "nCmd": 16,
        "strSN": "260029"
}
```

返回`json`数据

```json
{
    "result":{
        "strSN":"260029",
        "nCmd":16,
        "nID":288,
        "status":0,
        "message":"Success."
    }
}
```

根据cmdID 请求耗时操作的执行结果

```json
{
        "nCmd": 288,
        "strSN": "260029"
}
```

返回的结果

```json
{
    "result":{
        "strSN":"260029",
        "nID":288,
        "status":0,
        "message":"Success." //（-1 unRun, 1 Runing ,0 Finished success）
    }
}
```





### 初始化打印机

`json`指令：

```json
{
     "nCmd": 3,
     "strSN": "260029"
}
```

返回的`json`数据

```json
{
    "result":{
        "message":"Success.",
        "nCmd":3,
        "status":0,
        "strSN":"260029"
    }
}
```
### 获取任务(历史)列表
`json`指令：`nType`为0则为任务列表，1则为历史列表

```json
{
    "nCmd":5,
    "strSN":"260029",
    "args":{
        "nType":0    // 0任务列表 1历史列表
    }
}

```

返回的`json`数据

```json
{  
  "result":{
        "nCmd":5,
        "status":0,
        "message":"Success.",
        "result":{
            "currentjob":"0",
            "printerStatus":"1",
            "list":[
                {
                    "jobid":89,
                    "taskid_list":[
                        39
                    ],
                    "taskname_list":[
                        "cube"
                    ],
                    "hostname":"GJH_PC",
                    "date":"2018-11-30 18:08:55",
                    "printtimes":140,
                    "jobstatus":0,
                    "weight":0.401571
                },
                {
                    "jobid":90,
                    "taskid_list":[
                        39
                    ],
                    "taskname_list":[
                        "cube"
                    ],
                    "hostname":"GJH_PC",
                    "date":"2018-11-30 18:08:55",
                    "printtimes":140,
                    "jobstatus":0,
                    "weight":0.401571
                },
                {
                    "jobid":91,
                    "taskid_list":[
                        39
                    ],
                    "taskname_list":[
                        "cube"
                    ],
                    "hostname":"GJH_PC",
                    "date":"2018-11-30 18:08:55",
                    "printtimes":140,
                    "jobstatus":0,
                    "weight":0.401571
                },
                {
                    "jobid":92,
                    "taskid_list":[
                        39
                    ],
                    "taskname_list":[
                        "cube"
                    ],
                    "hostname":"GJH_PC",
                    "date":"2018-11-30 18:08:55",
                    "printtimes":140,
                    "jobstatus":0,
                    "weight":0.401571
                }
            ]
        }
    }
}

```

### 移动任务列表

`json`指令: `nJobId` 任务编号，`bDown` 1向下 0向上

```json
{
        "nCmd": 8,
        "strSN": "260029",
        "args": {
            "nJobId": 23,
             "bDown":1
        }
}
```



### 重复打印历史任务

`json`指令：

```json
{
        "nCmd": 13,
        "strSN": "260029",
        "args": {
            "nJobId":[12,34], // 可以添加多个 
            "nTime":1  		  // 重复打印的次数
        }
}
```

返回的`json`数据

```json
{
    "result":{
        "strSN":"260029",
        "nCmd":13,
        "status":0,
        "message":"Success."
    }
}
```





### 删除打印任务

`json`指令：

```json
{
    "nCmd":6,
    "strSN":"260029",
    "args":{
        "nType":0, 
        "nJobId":2
    }
}
```

返回的`json`数据

```json
{
    "result":{
        "strSN":"260029",
        "nCmd":6,
        "status":0,
        "message":"Success."
    }
}

```

### 从打印任务中启动打印
`json`指令：

```json
{
    "nCmd":10,
    "strSN":"260029",
    "args":{
        "nJobId":2
    }
}

```

返回的`json`数据

```json
{
    "result":{
        "strSN":"260029",
        "nCmd":10,
      	"nID":258,
        "status":0,
        "message":"Success."
    }
}

```

### 发送打印任务到打印机
`json`指令：

```json
{
    "nCmd":30,
    "strSN":"260029",
    "strPath":"/home/task/tiertime.tsk";
}
```

返回的`json`数据

```json
{
    "result":{
        "strSN":"260029",
        "nCmd":30,
        "status":0,
        "message":"Success."
    }
}

```

### 获取当然打印任务信息

`json`指令

```json
{
		"nCmd":7,
		"strSN":260029
}
```

返回值：

```


```



### 打印中控制操作(暂停、继续、停止)

`json`指令：`nType` : 1).暂停     2).停止     3).继续

```json
{
        "nCmd": 12,
        "strSN": "260029",
        "args": {
            "nType": 1
        }
 }
```

返回的`json`数据

```json
{
    "result":{
        "strSN":"260029",
        "nCmd":12,
        "nID":259,
        "status":0,
        "message":"Success."
    }
}
```

### 获得打印机状态

`json`指令

```json
{
        "nCmd": 4,
        "strSN": "260029",
}
```

返回的`json`数据,dNozzleTemperature和dFlatTemperature小于零为，正在打印中打印温度的百分比。

```json
{
	"result":{
      "nPrinterStatus":	2,
      "nSystemStatus":	2,
      "dNozzleTemperature":	0.980000,
      "dFlatTemperature":	0.680000,
      "nRemainWeight":	483,
      "nJobID":	17,
      "nJob_RemainTime":	3083,
      "nJob_Percent":	48,
      "nWiFiStatus":	2,
      "nLanStatus":	0,
      "nUsbIsMaster":	0,
      "bBasePlatHeat":	true,
      "bNozzleHeat":	true,
      "bLockStatus":	false,
      "strMaterial":	"ABS"
	}
}
```

