# API Guide

Print server/server refers to the computer that is running Wander Server program.

## Update Log

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
    <td>Printer Command</td>
  </tr>
  <tr>
      <td>...</td>
      <td>2018-2-20</td>
      <td>GJH</td>
      <td>Added work flow for estimated print time</td>
  </tr>
  <tr>
      <td>...</td>
      <td>2019-7-4</td>
      <td>GJH</td>
      <td>Added work flow for print and print control</td>
  </tr>
  <tr>
    <td>V0.1.0</td>
    <td>2019-9-30</td>
    <td>GJH</td>
    <td>Added New Wander Server API</td>
  </tr>
  <tr>
    <td>....</td>
    <td>2019-10-09</td>
    <td>GJH</td>
    <td>Added Connector Printer API</td>
  </tr>
  <tr>
    <td>...</td>
    <td>2019-10-15</td>
    <td>GJH</td>
    <td>Add new command to control printer</td>
  </tr>
</table>





### Search for USB connection

Only for searching all devices connected through USB on the server. No data return.

`{"cmd":"searchusb"} `

feedback

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

### Return the server side connected USB devices 

Only return search results, no search actions.

`{"cmd":"usbdevlist"}`

feedback：

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

### Search for online network devices

Only search, no result returned.

`{"cmd":"searchnet"}`

feedback：

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

### Return server side connected network devices

Only for get the result of search, no search action.

`{"cmd":"netdevlist"}`

feedback：

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

### Get all online devices（USB+NetWork）

Only return result, no search.

`{"cmd":"searchall"}`

feedback：

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

### Connect USB Printer

For connecting device connected through USB

`{"cmd":"usbconnect,"sn":"260029"}`

feedback

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



### Connect Network Printer

For connecting device connected through Network

` {"cmd":"netconnect","sn":"260029"}`

feedback

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



### Disconnect

For disconnecting devices already connect to the server

` {"cmd":"disconnect","sn":"260029"}`

feedback

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

### Get Printer Status

Get status that connected to the server （connected by"usbconnect" or "netconnect"）

`{"cmd":"getprintstatus","sn":"260029"}`

feedback

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



### Initialized Printer

Initialize connected printer

`{"cmd":"exec","sn":"260029","action":"initprinter"}`

feedback

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

### Get print job name

`{"cmd":"exec","sn":"260029","action":"jobcurrent"}`

feedback

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



### Pause Print Job

Pause print job of connected server.

客户端暂停服务端在线并且正在打印的打印机。

`{"cmd":"exec","sn":"260029","action":"pauseprint"}`

feedback

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



### Resume Printer

For connected paused printer, resume its print job.

`{"cmd":"exec","sn":"260029","action":"resumeprint"}`

feedback

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

### Stop Print Job

stop print job of connected printer.

`{"cmd":"exec","sn":"260029","action":"stopprint"}`

feedback

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

### Auto Nozzle Height

Trigger auto nozzle height measure. 

`{"cmd":"exec","sn":"260029","action":"autoheight"}`

feedback

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

### Auto level

Trigger auto leveling of printer

`{"cmd":"exec","sn":"260029","action":"autoplat"}`

feedback

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



### Get history print job list 

（History = printed print jobs）

get the history list of connected printer

`{"cmd":"exec","sn":"260029","action":"historylist"}`

feedback

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



### Get Print Job List

`{"cmd":"exec","sn":"260029","action":"joblist"}`

feedback

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

### Delete Print Job

User for deleting print job on the job lists.

PS："type": 0 refer to print job list, type 1 refer to history list.

`{"cmd":"exec","sn":"260029","action":"jobdelete","jobid":16,"type":0}`

feedback

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



### Move Print Job Priority

This command move print job up or down on the print job lists.

`{"cmd":"exec","sn":"260029","action":"adjustjob","jobid":12,"down":true}`

feedback

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



### Upload File to Server

The command is used on client side, to upload file to printer server.

PS: data refer to the binary content of file.

`{"cmd":"uploadfile","filename":"cube.tsk","data":"........"}`

feedback

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



### Send Print Job to Printer

Send uploaded print job to printer

```json
{
	"cmd": "exec",
	"sn": "260029",
	"action": "sendtaskfile",
	"filepaths": ["/var/folders/g8/z8kmspv509gbw48_8wtzp7sw0000gn/T/cube.tsk"],
	"username": "gjh_web"
}
```

feedback

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



### Check Printability

To check if the print job is printable on target machine. Including eg. material, machine model and extruder.

`{"cmd":"exec","sn":"260029","action":"jobcanprepare","jobid":3}`

feedback

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



### Prepare for Print Job Initiation

For after printability check, prepare print job data for printing.

`{"cmd":"exec","sn":"260029","action":"jobprepare","jobid":3}`

feedback

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



### Start Print Job

For after print job data preparation, initiate print job.

`{"cmd":"exec","sn":"260029","action":"jobprint","jobid":3}`

Feedback

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



### Prepare and Start Print Job

This command equals to running the 3 commands above in one run. The program will do following actions: Printability Check>Data Preparation>Start Print Job.

`{"cmd":"exec","sn":"260029","action":"jobprepareprint","jobid":3}`

feedback

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



### The Work Flow for Printing Local Print Job

For a local print job, the user must go through following steps:

Upload local print job to print server => Send print job on print server to printer => Prepare and start print job that is sent to printer.



### Get Info of Materials Save in Printer

This command get all the info of material information save in printer.

`{"cmd":"exec","sn":"260029","action":"getmaterials"}`

feedback

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



### Get Current Material Info

Get detailed info of currently selected material on printer.

该指令用于获取当前设置材料的详细信息。

`{"cmd":"exec","sn":"260029","action":"getcurmaterial"}`

feedback

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



### Set Printer Material

Set printer material 

matid is equal to the "type" of material info. Weight unit is gram

`{"cmd":"exec","sn":"260029","action":"getcurmaterial","matid":66286,"weight":999}`

feedback

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



### Reset Printer SD Card

For reseting SD card, including materials and languages.

`{"cmd":"exec","sn":"260029","action":"resetsdcard"}`

feedback

```json
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





### Homing of Continuously Build Platform

This command is only usable on X5 or similar model，homing of platform.

`{"cmd":"exec","sn":"450899","action":"resetplat"}`

feedback

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



### Change Build Plate

This command is only compatible to X5 or similar models, change a new build plate from plate holder.

`{"cmd":"exec","sn":"450899","action":"platechange"}`

feedback

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



### Switch for Side Door

This command is only compatible to X5 or similar models, open or close sider door.

`{"cmd":"exec","sn":"450899","action":"sidedooropen"}`

feedback

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



### Continuous Printing

This command is only compatible to X5 or similar models，Set or read continuous printing.

read continuous printing status `{"cmd":"exec","sn":"450899","action":"autoprintflag"}`	

set continuous printing status `{"cmd":"exec","sn":"450899","action":"autoprintflag","set":1,"value":1}`

feedback

```json
// read status
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

// set status
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


