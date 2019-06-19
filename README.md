# Linux
**This a linux study notes**
# 系统安装

# linux系统使用相关
  * 远程登录
  直接用putty 输入地址和密码
  * 下载文件
  用filezilla ![png](https://i.loli.net/2019/06/19/5d09971acbaaa69134.png)
  
# 常用命令
## 后台运行程序
1. 可以用screen软件开多窗口，但是永久了感觉容易误操作
![png](https://i.loli.net/2019/06/19/5d099a59b3f4a25324.png)
2. nohup后台运行
`nohup /data1/tangx/anaconda3/bin/python3 -u blstm+crf.py > log.out 2>&1 &` 后台运行python脚本 `-u` 可以显示脚本里的`print`函数输出， 日志输入到`log.out`里面

## 修改命令快捷键
使用 `alias`命令   比如 `alias h='history'` 

## 添加环境变量
进入bashrc  `vim ~/.bashrc` , 再最后一行加入 `export PATH=$PATH:/data1/tangx/software/FastQC/` 
![1](https://i.loli.net/2019/06/19/5d0999f0a2e3453859.png)

## 查看进程线程，核心使用情况
安装 htop后输入htop 
`cat /proc/cpuinfo | grep name | cut -f2 -d: | uniq -c` 查看cpu型号

## 结束程序 
`ps -ef |grep blstm+crf.py` 查看关于blstm+crf的进程， 找到uid, 使用 `kill -9 xxxxx` 结束进程

## 重定向任务
![png](https://i.loli.net/2019/06/19/5d09992a3bfe972411.png)

## 文件解压命令
`tar -xjvf file.tar.bz2 //解压 tar.bz2 `      
`tar zxvf *.tar.gz`    
`gunzip *.gz `    

## 查看目录层级
`tree -L X  #选择查看几层目录`
## 统计目录文件数量
`ls -l |wc -l`
##
