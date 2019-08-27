# Linux
**This a linux study notes**
## 目录
-[linux系统相关](#linux系统使用相关)       
-[常用命令](#常用命令)
-[软件使用](#软件使用)




# linux系统使用相关
  * 远程登录
  直接用putty 输入地址和密码
  * 下载文件
  用filezilla ![png](https://i.loli.net/2019/06/19/5d09971acbaaa69134.png)

 * 根目录
 ![linux.png](https://i.loli.net/2019/08/27/yWuZESdxJvLzq6f.png)



# 常用命令

## 基础命令

### cat命令	
cat命令的用途是连接文件或标准输入并打印
命令的功能	1. 一次显示整个文件：cat filename
	2. 从键盘创建一个文件： cat > filename  只能创建新文件，不能编辑已有的文件
	3. 将几个文件合并为一个文件： cat file1 file2 > file
 
### sort命令
 
sort将文件的每一行作为一个单位，相互比较，比较原则是从首字符向后，依次按ASCII码值进行比较，最后将他们按升序输出。
	打印输出
-u	去除重复行
-r	改为降序
重定向写入文件	sort filename > newfile ; 但是不改变原文件
-o	可以将重定向的的结果写入原文件
-n	以数值来排序 ；例： 排序 10 2    加上-n 就2<10 ;不加就10< 2

 
### uniq命令
uniq命令	uniq命令可以去除排序过的文件中的重复行，因此uniq经常和sort合用。也就是说，为了使uniq起作用，所有的重复行必须是相邻的。
-d	只显示重复的行
-c	sort testfile | uniq -c    排序之后删除了重复行，同时在行首位置输出该行重复的次数
排序去重	cat words | sort |uniq    

### wc统计文本
wc文本统计	word count
wc /etc/passwd	40   45 1719 /etc/passwd 40是行数；45是单词数；1719是字节数

### tr命令

tr命令	转换或删除字符，字符处理命令
工作原理 	tr [OPTION]... SET1 [SET2]  不接受直接输入文件，需要重定向
tr 'ab' 'AB'	将文本中 ab 都换为AB  
-d	 tr -d 'ab'  表示删除字符



## 后台运行程序
1. 可以用screen软件开多窗口，但是永久了感觉容易误操作
![png](https://i.loli.net/2019/06/19/5d099a59b3f4a25324.png)
2. nohup后台运行
`nohup /data1/tangx/anaconda3/bin/python3 -u blstm+crf.py > log.out 2>&1 &` 后台运行python脚本 `-u` 可以显示脚本里的`print`函数输出， 日志输入到`log.out`里面

## 修改命令快捷键
使用 `alias`命令   比如 `alias h='history'` 

### history添加时间
```bash
HISTFILESIZE=2000      #设置保存历史命令的文件大小
        HISTSIZE=2000          #保存历史命令条数
        HISTTIMEFORMAT="%Y-%m-%d:%H-%M-%S:`whoami`:  "    #记录每条历史命令的执行时间和执行者
        export HISTTIMEFORMAT
```

## 添加环境变量
进入bashrc  `vim ~/.bashrc` , 再最后一行加入 `export PATH=$PATH:/data1/tangx/software/FastQC/` 
![1](https://i.loli.net/2019/06/19/5d0999f0a2e3453859.png)
![huanjing.png](https://i.loli.net/2019/08/27/6usQWeo2DcMYEmL.png)
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


## 命令提示符修改

进入`~/.bashrc`后修改为
```bash
if [ "$color_prompt" = yes ]; then
PS1="\[\e[32;1m\]\u@\h \e[31;1m\]\t \[\e[33;1m\]\w \n\$\[\e[;m\] "
else
PS1="\[\e[32;1m\]\u@\h \e[31;1m\]\t \[\e[33;1m\]\w \n\$\[\e[;m\] "
fi
```
# 软件使用

## windows 远程 linux下的jupyter
```bash
nohup jupyter-lab --no-browser --NotebookApp.token='' >/dev/null 2>&1 &

ssh -N -L 8888:localhost:8888 tangx@服务器地址

```
