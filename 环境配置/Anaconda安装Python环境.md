# python文件安装
   1. 安装环境下载
   [python下载](http://www.python.org)
   2. 环境变量配置
   将python安装目录增加到path路径下


# Anaconda安装
 1.下载[Anaconda](https://www.anaconda.com/download/)
 2.查看已安装的库
    ```
    conda list
    conda install numpy
    ```
 3.安装不确定库
   ```
   anaconda search -t conda tensorflow
   anaconda show jjhelmus/tensorflow
   ```



## 1.创建python环境
```
conda create --name testEnv python=3.4
```
## 2.激活环境
```
activate testEnv  #win
source activate testEnv  #linux or mac
```

## 3.返回默认环境
```
deactivate testEnv testEnv #win
source deactivate testEnv testEnv #linux or mac
```

## 4.删除一个已有的环境
```
conda remove --name testEnv --all
```

## 5.conda包管理
- 安装包
```
conda install 包名
```
- 查看已有包
```
conda list
```
- 查找包信息
```
conda search 包名
```
- 指定环境安装,更新,删除包
```
conda install -n testEnv numpy
conda update -n testEnv numpy
conda remove -n testEnv numpy
```

## 更新conda 
```
# 更新conda，保持conda最新
conda update conda

# 更新anaconda
conda  update anaconda

# 更新python
conda update python
# 假设当前环境是python 3.4, conda会将python升级为3.4.x系列的当前最新版本
```


## 设置镜像
```
# 添加Anaconda的TUNA镜像
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
# TUNA的help中镜像地址加有引号，需要去掉
 
# 设置搜索时显示通道地址
conda config --set show_channel_urls yes
```




## 设置 Anaconda默认路径
![](https://github.com/anbylau2130/gitnote/tree/master/%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/images/5c3c1464b8ed3759cb000000.png)