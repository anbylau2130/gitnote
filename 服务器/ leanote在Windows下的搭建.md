
# 下载准备

 1. 下载[leanote](http://leanote.org)
 2. 下载[MongoDB](https://www.mongodb.com/download-center?jmp=nav#community)

----------


# 安装MongoDB
1.在c盘根目录下建立data目录，在data目录下建db目录
2.运行命令行
```
    cd c:\Program Files\MongoDB\Server\3.4\bin
    mongod
```

3.导入leanote数据库
```
cd c:\Program Files\MongoDB\Server\3.4\bin

mongorestore -h 127.0.0.1-d leanote --dir c:\leanote\mongodb_backup\leanote_install_data
```

----------


# 运行leanote服务

```
cd C:\leanote\bin
run
```

#访问web网站
http://IP:9000
默认管理员账号为admin，密码为abc123

#设置开机启动
做到这里，leanote已经正常运行，但是cmd还开着一个mongod运行，并且在电脑重启后，还需要再依次运行mongod、leanote server才能够启动，所以接下来要让MongoDB和leanote server在系统开机时，自动运行。

一、添加环境变量
进入系统属性->高级->环境变量，在“系统变量”中找到Path，在最后增加

;c:\Program Files\MongoDB\Server\3.4\bin

注意前边有个分号。路径按照自己安装MongoDB的实际路径填写。 
打开一个cmd，输入

mongo -version

如果能够正常打印版本信息，则成功：

二、添加mongodb服务
在c:\data下新建一个log文件夹，在cmd下输入

mongod --logpath=C:\data\log\mongodb.log --install

在【开始菜单】下的【运行】中输入命令services.msc，找到“mongodb”服务，启动

三、添加leanote的run.bat服务
待续…

 