# 基础命令

## 获取python版本

~~~python
python --version
~~~



## 运行python程序

如果要运行helloworld.py程序，则输入命令：

~~~python
python helloworld.py
~~~



## 运行python交互式编程

~~~python
python
~~~

程序就能进入到python的交互式编程界面，可以输入一行执行一行。



## 退出python交互式编程

~~~python
exit()
~~~

在Python命令行环境下，执行exit()后可以退出python。

# 基础设置

## Linux下改变默认Python为Python3

Linux下默认安装了Python2和Python3，每次要执行python程序时，如果输入python xxx.py的话，默认的是Python2，要用Python3来执行程序，需要输入python3 xxx.py。

为了让系统将Python默认为Python3，可以这么做：

先看看有几个版本的Python：

~~~bash
ls /usr/bin/python*
~~~

输出为：

~~~bash
pi@raspberrypi:~ $ ls /usr/bin/python*
/usr/bin/python     /usr/bin/python2.7-config  /usr/bin/python3           /usr/bin/python3.7m         /usr/bin/python3m
/usr/bin/python2    /usr/bin/python2-config    /usr/bin/python3.7         /usr/bin/python3.7m-config  /usr/bin/python3m-config
/usr/bin/python2.7  /usr/bin/python2-pbr       /usr/bin/python3.7-config  /usr/bin/python3-config     /usr/bin/python-config
~~~

可以看到系统同时安装有Python2和Python3。

### 方法1

执行命令：

~~~bash
alias python="/usr/bin/python3"
~~~

那么再执行**python --version**命令时，会显示Python3。但是这个只是临时的，系统重启后，会又恢复到原来的版本状态。

要实现全局一直有效的修改的话，修改/etc/bash.bashrc文件，在文件的末尾添加下面这两行：

```py
alias python=python3
alias pip=pip3
```

系统重启后，可以看到Python默认就指向了Python3。

### 方法2

先移除python-is-python2， 再安装python-is-python3。

~~~bash
sudo apt purge python-is-python2
sudo apt install python-is-python3
~~~

## 如何让系统直接执行Python脚本

在Linux/Unix系统中，只需要在脚本顶部添加一行语句#! /usr/bin/env python3，就让Python脚本可以像SHELL脚本一样可直接执行。

以hello.py文件为例，在该文件的第一行加上 **#! /usr/bin/env python3**：

~~~python
#! /usr/bin/env python3
print ("Hello, Python!");
~~~

然后，改变hello.py为可执行文件：

~~~bash
chmod +x hello.py
~~~

然后测试一下hello.py是否变成了可执行文件，直接执行hello.py，不需要再在前面加python就可以执行python脚本：

~~~bash
./hello.py
~~~

可以看到，系统可以输出字符串：

~~~
Hello, Python!
~~~

