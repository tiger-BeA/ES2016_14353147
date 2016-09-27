# DOL配置
-------------------

##Description

>**Distributed operation layer (DOL)** is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

##How To Install


####安装必要环境

```
$ sudo apt-get update
$ sudo apt-get install ant
$ sudo apt-get install openjdk-7-jdk
$ sudo apt-get install unzip
```
#### 下载文件

```
$ sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
$ sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
```
#### 解压文件
1. 新建dol的文件夹

	```
	$ mkdir dol
	```
	
2. 将dolethz.zip解压到 dol文件夹中

	```
	$ unzip dol_ethz.zip -d dol
	```
3. 解压systemc

	```
	$ tar -zxvf systemc-2.3.1.tgz
	```
		
#### 编译systemc
1. 解压后进入systemc-2.3.1的目录下
	```
	$ cd systemc-2.3.1
	```

2. 新建一个临时文件夹objdir
	```
	$ mkdir objdir
	```
3. 进入该文件夹objdir
	```
	$ cd objdir
	```

4. 运行configure（能根据系统的环境设置一下参数，用于编译）
	```
	$ ../configure CXX=g++ --disable-async-updates
	```
下图为运行configure之后的截图		
&nbsp;
<br/>
5. 编译

	```
	$ sudo make install
	```

	编译完后文件目录如下(`$cd .. `      `$ls`)
	&nbsp;![Alt text](./1474970226419.png) 
	<br/>
6. 记录当前的工作路径（会输出当前所在路径，记下来，待会有用）

	```
	$ pwd
	```
	
#### 编译dol
1. 进入刚刚的dol文件夹，修改build.xml文件
找到下面这段话，就是说上面编译的systemc位置在哪里

	> property name="systemc.inc" value="YYY/include"
	> property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/

	把YYY改成上页pwd的结果（**注意，对于  64位 系统的机器，lib-linux要改成lib-linux64**）
<br/>
2. 编译

	```
	$ ant -f build_zip.xml all
	```
	若成功会显示build sucessful
	<br/>
3.  运行第一个例子<br/>
	进入build/bin/main路径下
	
	```
	$ cd build/bin/main
	```
然后运行第一个例子
	```
	$ ant -f runexample.xml -Dnumber=1
	```
	成功结果如图所示
&nbsp;![Alt text](./嵌入1.PNG)

---------
摘自 <a>嵌入式Lab2 版本控制& 文档</a>

