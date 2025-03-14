+++
date = '2025-03-08T23:15:08+08:00'
draft = false
title = 'Windows环境下终止80端口上的所有进程'
+++

# killPort80Pid
终止80端口上的所有进程，杀死80端口占用的进程,在Windows环境下
如果要终止其它端口的进程，只需修改脚本中的端口号80为其它端口号即可。

项目地址：
https://github.com/jiangjilu/killPort80Pid.git

## 现在可以直接下载bat文件运行
下载项目中的 killPort80Pid.bat 到电脑上运行即可。


## 起因

我们在Windows环境下开发时，经常用到80端口来开启网关服务，

例如：使用宝塔面板时要使用到 Nginx 但是每次开机后Nginx经常会起不来，这是因为开机时有其它程序占用了80端口。

也有各种其它情况：
开发者：在开发Web应用时，可能需要重启服务器，而有时手动停止服务失败或者服务未能正常关闭时，就需要用到这种方法来清理端口占用，以便重新启动服务。

**系统管理员：** 当遇到服务器性能问题，发现有不明进程占用了80端口（默认HTTP服务端口），可能需要清理这些进程以解决冲突或安全问题。

**网站维护人员：** 在部署新的Web服务或迁移网站时，可能需要确保旧的服务已经被正确关闭，特别是当新旧服务需要在同一机器上运行且使用相同端口时。

**安全研究人员：** 在进行系统安全检查时，如果发现有恶意软件或未授权的服务在80端口运行，他们会采取措施终止这些进程以保护系统安全。

**共享主机用户：** 在一些共享主机环境，用户可能需要管理自己的服务，当发现端口冲突时，可能需要手动干预。


## 自动找到并终止指定端口（例如80）上的所有进程，你可以使用批处理脚本（在Windows环境下）,请按照以下步骤操作：

1、打开记事本或任何文本编辑器。

2、复制并粘贴以下脚本：

```cmd
@echo off
set "port=80"
for /f "tokens=5" %%i in ('netstat -ano ^| findstr :%port%') do (
    if not errorlevel 1 (
        taskkill /F /PID %%i
    )
)
```

3、将文件保存为扩展名为.bat的文件，比如 killPort80Pid.bat 。

4、右键点击该批处理文件，选择“以管理员身份运行”。

## 批处理脚本工作原理是：

@echo off 关闭命令回显，使输出更整洁。

set "port=80" 定义要查找的端口号。

for /f "tokens=5" %%i in (...) do (...) 循环通过netstat -ano | findstr :%port%命令获取到的每一行，并提取出第5个token（即进程ID）。

taskkill /F /PID %%i 强制终止每个找到的进程。
