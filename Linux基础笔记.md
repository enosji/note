# 1、操作系统的基本概念

## 1.1、Windows与Linux的关系

当前主流的操作系统：Windows、android、ios、symbian、unix \linux

windows：傻瓜式、好学习

Linux：Linux认为每个用户都是专业人士，操作麻烦，学习难度大，免费的，开源的，性能好，可移植性好，好的设计理念

Android：移动操作系统，Android基于Linux

iOS：很优秀，创造性

嵌入式操作系统：Linux+WinCE

当前运用领域：消费电子Android，工业linux

## 1.2、多机开发：双系统和虚拟机

开发嵌入式程序需要Linux环境。但是因为Windows中有很多很好用的软件，如notepad++，sourceinsight，所以我们也需要Windows。

既需要Windows又需要Linux。

第一种：双系统：两个系统来回切换不方便

第二种：虚拟机：方便，损失性能，与真机有微弱的差距

第三种：两台电脑：不方便

现实中：对于个人开发者来说虚拟机更方便，大公司是用服务器+客户端

## 1.3、搭建开发环境

虚拟机软件：单纯在Windows环境下运行的常规软件，主流的虚拟机软件有VMware和virtualbox

虚拟机软件在Windows上运行来模拟一台电脑，在虚拟机中安装别的操作系统

## 1.4、隐藏文件和非隐藏文件

Windows中文件的隐藏与不隐藏是通过修改文件属性实现的。

Linux中：隐藏文件的特点是文件名前面以“.”开头，跟属性无关，在Linux中查看隐藏文件要用 “ls-a” 显示隐藏文件

## 1.5、相对路径与绝对路径

什么是路径：路径是用来标识一个文件在操作系统中的文件系统中存储位置的。pathname

例如：D:\winshare\enum.c  就是一个全路径pathname

 D:\winshare        就是路径      path

 enum.c              就是文件名    name

绝对路径：是从绝对位置开始的。  例如在Windows中从某一个盘符开始的 （C:\），Linux中从根目录“\”开始的。

举例：

/abc/123/def.txt   是Linux中的绝对路径

Abc/123.def.txt   不是Linux中的绝对路径

相对路径：指明路径的时候，从当前路径位置开始。

举例：D:\我的文档\abc\abc.txt

 D:\我的文档\123\123.txt

 当前在123.txt要去abc.txt

方法一：使用绝对路径。直接给出abc.txt的绝对路径 D:\我的文档\abc\abc.txt

方法二：采用相对路径。从当前路径开始往上走一层（abc）再往下走一层就到了 。../abc/abc.txt

# 2、Linux基础知识与技能

## 2.1、Linux的内核、发行版

Linux本身指的是一个操作系统的内核，只有内核是无法直接使用的，我们需要的是包含了内核和一批应用程序的一个集合体。这个就叫Linux的发行版。

Ubuntu、Redhat就是Linux的不同发行版。

## 2.2、GUI（图形用户界面）和comdline(命令行)

GUI：grahics user interface ,图形用户界面。

comdline：command line ,命令行。

人机交互：人和机器（计算机）进行交互，常用的有命令行和GUI

Windows和Linux都是既有GUI又有命令行的，但是前者主要是GUI后者主要是命令行

## 2.3、Linux使用技巧

### 1、使用Tab键输入

### 2、Linux命令行中一些符号的含义

​	.			代表当前目录

​	..		   代表上一层目录，当前目录的父目录

​	-			代表前一个目录，我刚才是从哪一个目录过来的

​	~			代表当前用户的宿主目录

​	$			普通用户的命令行提示符

​	#			root用户的命令行提示符 

​	*			万能匹配符

宿主目录：就是操作系统为当前用户所设计的用来存放文件、工作的默认目录如Windows中的“我的文档”就是Windows中的宿主目录。Linux中每个用户都有自己的宿主目录，这个目录对于普通用户来说在/home/username/,对于root用户来说在/root。			

## 2.4、Linux常用命令

### (1) ls  (list ,列表)

作用：使用列表把当前文件夹的内容显现出来

ls -a  显示所有文件包括隐藏文件

ls -l   以详细信息显示

显示详细信息时文件的前十个字符表示文件类型，后面9个字符表示文件权限。

第一个字符所代表的意义

“-” 表示是个普通的文本文件，指文本文件和二进制文件

“d” 表示文件夹，“d”时“directory”的缩写

“l” 表示时符号连接文件，，后面会用->打印出它指向的文件

“s” 表示scoket文件

“p” 表示管道文件 pipe

ls -l -a; ls -a -l; ls -la 都是可以的 效果会叠加

### (2) cd (change directory,更改目录)

作用：切换目录

涉及到相对路径和绝对路径

​	cd ..      ..代表上一层目录

​			.  代表当前目录

### (3) pwd (print work directory,打印工作目录)

作用：打印出当前的绝对路径

### (4) mkdir (make directory,创建文件夹)

作用：创建空文件夹

​	mkdir -p abc/def  创建级联文件夹

### (5) mv (move,移动)

作用：在目录间移动文件，重命名文件名

​	mv 源文件pathname 目标文件的pathname （移动和重命名可同时进行）

### (6) touch  

作用：创建空文件

​	touch pathname

### (7) cp (copy ,复制)

作用：复制文件或文件夹

​	cp 源文件pathname 目标文件pathname（可以复制和重命名同时进行））

​	cp -r 用来复制文件夹

​	cp -f 强制复制

实际操作时，一般用cp -f 复制文件 cp -fr 复制文件夹 （Linux中复制文件未成功系统不会告知所以一般都会用强制复制但是要小心它将有用的文件覆盖掉）

### (8) rm (remove,删除)

作用：用来删除文件和文件夹

​	rm 文件pathname

​	rm -r 文件间pathname

​	rm -rf (当删除不存在的文件时 加 f 和不加 f 返回值是不同的)

### (9) cat 

作用：直接在命令行中展示文件内容，也可以用来做输入

### (10)  rmdir (remove directory ,删除文件夹)

作用：与 rm -r 相比只能删除空文件夹

### (11) ln  (link,连接文件)

基础：Windows中快捷方式，实际上快捷方式和它所指向的那个文件是独立的两个文件，两个都占硬盘空间，只不过用户访问快捷方式时，其效果等同于直接访问指向文件。

Linux中有两种链接文件：

​	一种叫软连接（符号连接），等同于Windows中的快捷方式

​	一种叫硬连接

创建软连接文件：ln -s  源文件名 符号连接文件名

举例：ln -s abc.c cad.c  cad.c就是abc.c的符号连接文件，创建软连接源文件必须加绝对路径否则无法移动

硬连接的创建：ln 源文件名 符合连接名 

硬连接实际上和源文件在硬盘上是同一个东西，效果类似于硬盘上的一个文件，在文件系统上，在我们看来有好多个文件一样。每次删除一个文件时只要它还有其他硬连接的存在，这个文件就不会被删除，只有等连接文件都删除了，这个文件才会被删除。

### (12) man 

查询man手册，获取帮助信息

man 1 ls 代表你所要查的 ls 的命令

man 2 ls 代表你要查的 ls 的api

man 3 ls 代表你要查的 ls 的c库函数

### (13) apt-get

作用：用来在线安装卸载软件的程序

​	apt-get install vim 安装vim

​	apt-get remove vim 卸载vim

注意，安装和卸载软件都是在线的，你的Ubuntu必须能上网才能使用 apt-get 

说明：用 apt-get 安装软件的原来和必要性

Linux操作系统的发行版本，内核版本，定制性，造成Linux中软件的不兼容性。在Linux中安装软件是件困难的事情，装了软件不一定能用	。Ubuntu解决了这个问题，Ubuntu就适合某一个发行版的所有软件做了个列表，然后用户通过 apt-get install 安装软件时，服务器会根据你Ubuntu版本，给你下载合适的软件来安装，这样确保了软件的兼容性。

带来的问题：1、权限问题 2、虚拟机上不了网的问题

### (14)zo（打开这行）  zc（关闭折行）

在你想要折行的地方前后{{{   代码段  }}}

# 3、编辑器vi的使用（vi和vim的联系）

什么是编辑器？编辑器就是个软件，它的作用就是用来编辑。	例如编写文件，编写代码。

Windows中的常用的编辑器，如自带的notepad。比较好用的列如notepad++，UltraEditor。

Linux中常用编辑器，自带的最古老的vi，比较好用的vim，gedit。

注：vi和vim的关系：vim是vi的升级版。推荐使用vim

后面提到的vi就是vim

## 3.1、 vi的基础使用

（1）使用vi来打开/创建一个文件时，vi 文件名pathname

（2）vi的两种工作模式：

命令模式：当vi打开时默认为命令模式，要转入输入模式按“a”或“i”。在命令模式下，此时键盘上的输入的所有东西都被vi当作命令对待。

在命令模式下，最后不要乱输入。此时应该输入相应的命令，来让vi做相应的事情。

输入模式：用来向文件输入内容，可以从命令模式中按“a”或者“i”进入。输入完成后要先退回到命令模式（因为保存也是一种命令），在输入模式下按Esc键。

在命令模式下保存：

”:wq“	保存并退出

":w"	 只保存不退出

":q"	  之退出不保存

":q!"	不保存强制退出

":wq!"	保存并强制退出

## 3.2、 vi 的高级使用

### （1）查找

在命令模式下，输入“/ xxx“，就可以查找到xxx

### （2）快速切换行

在命令模式下，输入”：num“就可以快速切换到num行

### （3）设置显示行号

在命令模式下，输入”set nu“显示行号

设置不显示行号输入“set nonu”

设置永久显示行号，需要修改vi的配置文件。打开vi的配置文件~/.vimrc，在其中输入”set nu“即可。

### （4）行删除

在命令模式下，先将光标移动到要删除的行再输入”dd“

如果要删除连续的n行，使用”ndd“

### （5）行复制粘贴

复制：命令模式下，”nyy“复制n行的内容

粘贴：命令模式下，”p“

细节：复制时将光标放在粘贴行的第一行，粘贴是往当前光标的下一行进行粘贴

## 3.3、Linux中的权限表示&管理

### 3.3.1、普通用户和特权用户

Windows中有普通用户和特权用户，特权用户就是administered，普通用户可以有很多个。

特权用户时系统的管理员，对系统内所有文件具有操作权限，每个普通用户只能出来自己的文件不能访问其他用户的文件更不能随意处理系统文件。

Linux中也有普通用户和特权用户。普通用户权限受到限制，例如普通用户不能cd /root/，普通用户不能使用apt-get install 安装软件

可以使用”su 用户名“ 在不同的用户之间切换。

### 3.3.2、rwx与权限表示

ls -l    显示详细信息时

drwxrwxr-x，这10个字符，第一个字符表示文件类型，剩下的9个分成3组表示文件权限。

前三个表示此文件的属主对文件的权限

中间三个表示文件属主所在的组对文件的权限

最后三个表示此文件其他用户对文件的权限

“rwx”的解析：“r”代表可读，“w”代表可写，“x”代表可执行

rwx:可读可写可执行

r-x:可读不可写，可执行

r--:可读不可写不可执行

### 3.3.3、使用sudo暂时获取root权限

这个时Ubuntu的一个特点，在Ubuntu中使用sudo命令让普通用户暂时获取root用户的权限不必进行用户的切换

在需要用到权限的指令前面加入 sudo

# 4、Linux高级命令

## 4.1 、find 

在Linux文件系统中，用来查找一个文件放在哪里了。

find /ect -name "interfaces"  

总结：

（1）什么时候用：当你知道文件名，但是忘记它被放在哪个目录下，要找到该文件，用find

（2）怎么用：find 路径 -name "查找文件名"

文本替换：%s/worldname/new world name/g

选择文本替换：%s/worldname/new world name/gc

分屏：vsp+ filename

## 4.2、grep

功能：在一个文本文件中查找某一个词

举例：grep -nr “sum” *

总结：

（1）当你想查找某些符号在哪些地方（有可能是一个文件，或多个文件组成的文件夹）出现过就可以用grep

（2） 格式：	grep -nr ''要查找的符号'' 要查找的目录或文件集合

-n 表示查找结果显示行号

-r 表示要递归查找

## 4.3、which和whereis

功能：查找一个应用程序（二进制文件）在哪

举例：which ls      whereis ls

区别：which只显示二进制文件的路径，whereis显示二进制的路径和其源码或man手册位置

## 4.4、uname

功能：查看系统信息

## 4.5、开机和关机

shutdown -h now   立即关机

init 0                       关机

shutdown -r now    立即重启

reboot 

init 6                      重启

## 4.6、tree/lstree

功能：显示文件和目录由根目录开始的树形结构

## 4.7、mount/umount

功能：用来挂载磁盘的文件系统中

举例：mount -t nfs -o nolock 192.168.1.141:/root/rootfs/mnt  挂载磁盘

​		   umount /mnt 卸载磁盘

## 4.8、查询磁盘空间相关

df -h 显示已挂载的分区列表

du -h 文件名 列出文件或文件夹的大小，列出方式人比较好观察

## 4.9、用户管理

useradd user1 添加一个名字为user1的用户

userdel user1 删除一个名字为user1的用户

userdel user1 - - remove-home 彻底清除用户

password user1 为user1用户设置密码

sudo usermod -a -G 组名 用户名

## 4.10、权限管理

chmod   change mode 修改文件权限

chown    change owner 修改文件属主

chgrp     change group  修改文件属主所在组的权限

作用：用来管理文件系统中文件的权限的

drwxrwxr-x，这10个字符，第一个字符表示文件类型，剩下的9个分成3组表示文件权限。

前三个表示此文件的属主对文件的权限

中间三个表示文件属主所在的组对文件的权限

最后三个表示此文件其他用户对文件的权限

权限还有另外的表示方法，用数字来表示。

编码规则：

r       可读    数字编码  4

w      可写    数字编码  2

x       可执行 数字编码  1

--       无权限 数字编码  0

有了这个编码规则，则drwxrwxr-x 编码后 775

第一种修改文件的方法：

要把权限改成 drwxr-xr-x  对应的编码值为 755

修改命令为 chmod 755 文件名

第二中修改权限的方法：

在原来的权限基础上修改 增加或减少某些权限

三个组的用户的编码以此为：属主为u  属主所在的组为g  其他用户为o

例如

要增加属主可执行权限：chmod u+x

要增加属主所在组的可写权限 chmod g+w

要增加其他用户的可读权限 chmod o+r

文件权限掩码umask（002）

给文件设置权限时实际上是 777 | （~umask）所以一般就算给777的权限但是其他用户还是没有写的权限

## 4.11、文件的打包与解压缩

tar -czvf 压缩文件名.tar.gz  目标文件名  将目标目录文件打包成dir.tar.gz

tar -cjvf 压缩文件名.tar.bz2  目标文件名  将目标目录文件打包成dir.tar.bz2

tar -zxvf dir.tar.gz      解压缩dir.tar.gz

tar -jxvf dir.tar.bz2     解压缩dir.tar.bz2

## 4.12、网络配置命令

ifconfig                                         查询ip

ifconfig eth0 192.168.1.116          设置ip

ifconfig eth0 up                            启动网卡

ifconfig eth0 down                       禁用网卡

ifup eth0                                      启动网卡

ifdown eth0                                 禁用网卡

ifconfig eth0 192.168.1.116 netmask 255.255.255.0 同时设置ip和子网掩码

### 4.12.2、静态配置网络

1、 windows底下的网络适配器

​	网络和internel设置----->更改适配器--->找到有线网卡和无线网卡

2、ubuntu网络配置

​	 1）、虚拟机----》设置-----》网络适配器---》桥接模式---》确定

​	 2）、编辑---》虚拟网络编辑器----》如果菜单栏中没有三种模式的选择执行第3步
​	      ----》如果有三种选择---》选择VMnet0（桥接模式）----》已桥接至---》
​		  选择对应的联网的网卡底下的那一串英文字母-----》确定

​	 3）、编辑---》虚拟网络编辑器----》更改设置----》如果还没有三种选择---》还原默认设置

3、点击ubuntu右上角的网络图标-----》Edit connections-----》add----》create-----》
        Device MAC address选择-----》IPv4 setting----》menual ----》add----》ipaddr 
		----》netmask----》gateway----》DNS----》save

 4、测试

点击网络图标选择刚才配置好的网络适配器

  linux@linux:~/DC21031$ ping www.baidu.com

​		PING www.a.shifen.com (180.101.49.11) 56(84) bytes of data.
​        64 bytes from 180.101.49.11: icmp_seq=1 ttl=52 time=8.68 ms
​        64 bytes from 180.101.49.11: icmp_seq=2 ttl=52 time=9.44 ms
​        64 bytes from 180.101.49.11: icmp_seq=3 ttl=52 time=10.4 ms

5、ifconfig

查看网络配置信息

### 4.12.3、网络基础知识

ip地址      192.168.0.132    / 192.168.1.132   /192.168.2.132     192.168.x.y  (x取值0-255， y取值0-255)
192.168.0.1     当前网段下的第一主机是路由器

192.168.0.255   广播地址	

 2-254分配给我们主机的ip，DHCP服务就是让路由器分配一个空闲的ip给你的主机

子网掩码    255.255.255.0

网关   192.168.0.1  网关

### 4.12.4、命令行配置

 1、修改文件
      /etc/network/interfaces,添加如下内容：
	       auto eth0
           iface eth0 inet static
           address 192.168.1.111
           netmask 255.255.255.0
           geteway 192.168.1.1
           broadcast 192.168.1.255
           dns-nameservers 8.8.8.8 

 2、重启配置文件
        sudo service network-manager restart

## 4.13、虚拟机Linux上网的问题

### 4.13.1、VMware中的虚拟网络的三种设置

第一种：桥接 （bridge）

第二种：NAT

第三种：Host only  该模式下 仅主机可以上午 虚拟机不可以上网

### 4.13.2、虚拟机上网方式1：NAT方式

第一步：在菜单栏 虚拟机->设置->硬件->网络适配器，右侧选择NAT上网模式

第二步：vi /ect/network/interfaces，打开文件将文件中的static修改为dhcp 保存退出

第三步：执行/ect/init.d/networking restart 重启网卡

### 4.13.3、虚拟机上网方式2：桥接方式

第一步：在菜单栏 虚拟机->设置->硬件->网络适配器，右侧选择桥接模式

第二步：桥接到可以上网的网卡上，在菜单栏 编辑->虚拟网络编辑器，桥接到在windows中可以上网的网卡上（一般就是WiFi网络或者有线网络）

第三步：设置dhcp并重启网络：vi /ect/network/interfaces，打开文件将文件中的static修改为dhcp 保存退出，然后执行/ect/init.d/networking restart 重启网卡

### 4.13.4、总结

第一种NAT方式设置上网比较简单 ，但是不能用在嵌入式开发中。

第二章桥接设置上网比较繁琐，但是在嵌入式开发中比较有用。

## 4.14、shell指令

1、概念：
	    shell是一个命令行解析器，是将用户的指令转化为操作系统能够识别的指令。
        实现用户和操作系统之间的交互。
2、	shell的功能
          实现用户和操作系统交互
          保护内核	
3、工作的原理
        用户的请求或者指令发给shell，由shell将这个请求转化为内核能够识别的指令由内核控制硬件做出相应的操作，硬件将执行的结果通过shell返回给用户
4、shell的种类：
	   sh ：Bourne Shell（简称sh）：Bourne Shell由AT&T贝尔实验室的S.R.Bourne开发，也因开发者的姓名而得名。它是Unix的第一个Shell程序，早已成为工业标准。目前几乎所有的Linux系统都支持它。不过Bourne Shell的作业控制功能薄弱，且不支持别名与历史记录等功能。目前大多操作系统是将其作为应急Shell使用。

 csh ：C Shell（简称csh）：C Shell由加利福尼亚大学伯克利分校开发。最初开发的目的是改进Bourne Shell的一些缺点，并使Shell脚本的编程风格类似于C语言，因而受到广大C程序员的拥护。不过C Shell的健壮性不如Bourne Shell。

​      ksh ：Korn Shell（简称ksh）：Korn Shell由David Korn开发，解决了Bourne Shell的用户交互问题，并克服了C Shell的脚本编程怪癖的缺点。Korn Shell的缺点是需要许可证，这导致它应用范围不如Bourne Shell广泛。

​      bash：Bourne Again Shell（简称bash）：Bourne Again Shell由AT&T贝尔实验室开发，是Bourne Shell的增强版。随着几年的不断完善，已经成为最流行的Shell。它包括了早期的 Bourne Shell和Korn Shell的原始功能，以及某些C Shell脚本语言的特性。此外，它还具有以下特点：能够提供环境变量以配置用户Shell环境，支持历史记录，内置算术功能，支持通配符表达式，将常用命令内置简化。

## 4.15、bash功能命令

 上下键能够调出历史记录history 能够查看从系统启动到现在所有执行过的命令可以直接在命令行定义变量和给变量赋值
		linux@linux:~$ A=hello
        linux@linux:~$ echo $A
        hello
        linux@linux:~$ echo A
        A
6、shell命令体验
	    关机：sudo shutdown -h  now  立即关机
		      sudo shutdown -h  +50  “class is over”   50分钟以后关机
		重启：sudo shutdown -r   重启
              sudo reboot        重启
7、shell中的特殊字符
	   1）、通配符
	     ls 1*.c          匹配的是任意长度的字符，一个位置或者多个位置
		 ls 1[1-3].c      匹配1-3之间的任意字符，仅限一个位置
         ls 1[12].c       匹配有1或者有2的字符，一个位置
		 ls 1[^1.c      匹配除了1之外的所有的字符，一个位置
	  2）、管道
	     comd1 | comd2     将命令1的输出作为命令2的输入
		  ls /etc |wc -w    统计etc底下有多少个文件
		      wc -w 统计字段的个数，以空格分号这些隔开的
      3）、输入输出重定向
	      >          输出重定向，新建模式，不追加
		ls  -al /etc > file      将ls -al /etc的执行结果放入到file文件中
		  >>       输出重定向，追加模式，不会覆盖掉原先文件的内容，在文件的最后追加
		ls -a  >> file     
		 <          输入重定向
	       wc -l < file     将file文件中的内容作为输入，统计这个文件中的行数
	2>或者&>
	     ls 11111.c &>> file   将ls执行完的错误结果重定向到file文件中
	   标准输入：0

​		标准输出：1

​		标准输出：2

4）、命令置换
	     comd1  `comd2`   命令2的输出作为命令1的参数  
	          linux@linux:~/DC21031$ A=`pwd`
	          linux@linux:~/DC21031$ echo $A
	          /home/linux/DC21031
	          linux@linux:~/DC21031$ ls -al `pwd`		 

## 4.16、代码追踪调试符

`printf(“%s—-%s—%d\n”,__FILE__,__func__,__LINE__);`

`__FILE__`显示文件名

`__func__`显示函数名

`__LINE__`显示行号

## 4.17、du显示大小

df 显示磁盘分区使用率

du -h filename  显示文件夹大小

## 4.18进程管理

###     1、进程：

​	是一个动态的概念，程序运行时的状态，创建、调度、销毁。

### 	2、 程序：

​	存放在磁盘空间上的代码，是一个静态的概念。当你执行这个程序的时候会变成进程

### 	3、ps  查看linux系统当前运行的进程

​		ps -aux   可以列出当前系统运行的所有进程并且包含进程相关的信息

  USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
	       root         1  0.0  0.1   4576  1812 ?        Ss   08:58   0:01 /sbin/init
	       root         2  0.0  0.0      0     0 ?        S    08:58   0:00 [kthreadd]
	       root         3  0.0  0.0      0     0 ?        S    08:58   0:00 [ksoftirqd/0]

 			USER     进程所有者
 			  PID      进程的ID号，表明了当前系统中这个进程的唯一性
 			  %CPU     cpu占有率，永远达不到100%
 			  %MEM     虚拟记忆体的占有率
 			  VSZ      进程运行虚拟内存的大小
 			  RSS      进程运行占有内存的大小
 			  TTY      进程运行的终端
 			  STAT     进程运行的状态
 			  START    进程运行开始的时间
 			  TEME     进程运行的时间
 			  COMMAND  进程的名字

​	4、为了降低程序中while（1）对cpu的占有率

 						while(1)
 						{
 		  					 sleep(1);
 						}

### 	5、进程的状态

​			   D    uninterruptible sleep (usually IO)      不可中断的睡眠态
​	           R    running or runnable (on run queue)      运行态
​	           S    interruptible sleep (waiting for an event to 	complete)  可中断的睡眠态
​	           T    stopped, either by a job control signal or because it is being traced   停止态
​	           W    paging (not valid since the 2.6.xx kernel)    废弃掉了（内核2.6版本以后）
​	           X    dead (should never be seen)                   死亡态
​	           Z    defunct ("zombie") process, terminated but not reaped by its parent   僵尸态

 For BSD formats and when the stat keyword is used, additional characters may be displayed:

​			   <    high-priority (not nice to other users)      高优先级
​	           N    low-priority (nice to other users)           低优先级
​	           L    has pages locked into memory (for real-time and custom IO)   有页被所在内存中
​	           s    is a session leader                               会话组的领导者
​	           l    is multi-threaded (using CLONE_THREAD, like NPTL pthreads do)  进程中含有线程

​			  `+ `   is in the foreground process group      前台运行

### 6、后台运行程序

 		./a.out &    a.out到后台运行

### 7、杀死进程

​		 kill -9  PID   就可以杀死这个id的进程
​		 kill -l 显示kill这条命令所有的选项

### 8、pstree  以树形的方式显示当前系统运行的进程

 linux@linux:~/DC21031$ pstree
	        init─┬─ModemManager───2*[{ModemManager}]
	             ├─NetworkManager─┬─dnsmasq
	             │                └─3*[{NetworkManager}]
	             ├─VGAuthService
	             ├─accounts-daemon───2*[{accounts-daemon}]
	             ├─acpid

说明init是我们当前系统运行的第一个进程  

## 4.19 文件管理

### 1、文件系统

​	操作系统提供给我们组织和管理磁盘上的文件，并且提供用户交互接口。

### 2、常见的文件系统类型

####  1）、本地磁盘文件系统

​	实际存在于磁盘，包括硬盘、CD-ROM、DVD、USB存储器、磁盘阵列等。常见文件系统格式有：autofs、coda、Ext（Extended File sytem，扩展文件系统） 、Ext3、Ext4、VFAT、ISO9660（通常是CD-ROM）、UFS（Unix File System，Unix文件系统）、ReiserFS、XFS、JFS、FAT（File Allocation Table，文件分配表）、 FAT16、FAT32、NTFS（New Technology File System）等

#### 2）、网络文件系统

​	通过网络远程访问的文件系统，对于去访问的这个服务器来说，就是本地磁盘文件系统。常见文件系统格式有：NFS（Network File System，网络文件系统）、Samba（SMB/CIFS）、AFP（Apple Filling Protocol，Apple文件归档协议）和WebDAV等、ssh

#### 3）、虚拟/专用文件系统

​	标记为文件的进程，临时性，常见的在linux的目录/proc不驻留在磁盘上的文件系统。常见格式有：TMPFS（临时文件系统）、PROCFS（Process File System，
进程文件系统）和LOOPBACKFS（Loopback File System，回送文件系统）。

### 3、注意

​	   1）、目前Ext4是Linux系统广泛使用的一种文件格式。在Ext3基础上，对有效性保护、数据完整性、数据访问速度、向下兼容性等方面做了改进。

​       2）、最大特点是日志文件系统：可将整个磁盘的写入动作完整地记录在磁盘的某个区域上，以便在必要时回溯追踪。

### 4、SCSI与IDE设备命名

1）、sata硬盘的设备名称是“/dev/sda”

​	可以通过命令ls /dev/sd*来查看当前系统底下的scsi设备，显示/dev/sdaX(12345),这是系统盘如果你对系统盘做了操作，你的系统就会瘫痪

 2）、linux底下一切皆文件，u盘、键盘、摄像头，这些设备都会被系统识别成一个文件，这些文件都会存放到/dev这个目录下	  

3）、 /dev/sda1 含义是磁盘的分区

4）、IDE硬盘的设备名称是“/dev/hda”    /dev/hdX

###  5、linux文件系统架构讲解

根目录”/“下面的文件

​			bin:  存放系统一些可行文件
​            etc： 存放系统配置文件
​            boot：存放系统启动相关的文件
​            mnt： 通常作为挂载目录
​            dev： 设备挂载目录 dev/sd dev/video
​            proc: 存放标记为文件的进程，虚拟文件系统
​            home： 用户的家目录		
​            lib： 存放系统的库
​            media  多媒体设备

### 	6、文件属性  

​      1448803 drwxrwxr-x  2 linux linux  4096 Apr 19 11:36 .
​      1447541 drwxr-xr-x 28 linux linux  4096 Apr 19 13:34 ..
​      1448924 -rw-rw-r--  1 linux linux     0 Apr 16 03:11 111.c

1448924  inode号：表明了文件在文件系统中的唯一性（身份证号）

 文件类型（linux系统一共有七种文件类型bcd-lsp）

 b   块设备文件 （以块为单位读写，U盘、移动硬盘）

C   字符设备文件（以字节为单位读写）

d   目录文件

`-`   普通文件

l   链接文件

s   套接字文件（网络编程）

p   管道文件

## 4.20、shell脚本

1、shell

2、shell脚本

​	    shell命令的集合，通常加入一些控制语句，达到批量处理shell命令的效果

3、解释性语言

​	     shell脚本，从上到下依次执行，遇到错误退出或者执行完毕才结束
编译性语言C代码、jave这些代码文件，需要经过特定的编译器编译之后形成可执行的文件，再去执行可执行的文件，所以需要编译器、执行器。

 4、编辑shell脚本

​		 vi sh01.sh	
​           #!/bin/bash               告诉编译器解析这个脚本的shell种类

 5、执行shell脚本

方法一：给shell脚本可执行的权限
                  chmod 777 sh01.sh	
方法二：直接用bash来解析这个脚本文件
                  bash  sh02.sh （02.sh没有可执行权限）

6、shell常见的变量

​	1）用户自定义变量
​           注意一：用户自定义的变量超出一个字符，使用的时候用{}括起来表示一个整体用户自定义的变量都当作一个字符串

​	2）、位置变量

​	命令行参数
​			 $0         命令行参数的第一个
​             $1         命令行参数的第二个
​             ……
​             $9
​             ${10}      命令行参数的第10个
​             $@         命令行所有的参数，将命令行参数作为一个整体，不包含$0
​             $*			命令行所有的参数，将命令行参数挨个列出来,不包含$0

​	3）、预定义变量

​             $#         命令行参数的个数
​             $?         上一条命令执行的结果，0代表上一条命令执行成功，失败是任意值
​             $$	        当前进程的id号

​	4）、环境变量

 PATH       告诉编译器系统可执行命令在哪个位置 ，所有在终端执行的命令都是 从下面这些可执行的目录底下找的

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/opt/gcc-4.5.1/bin/

如果你给系统安装一些自己的软件或者工具链修改配置文件 vi  /etc/bash.bashrc
export PATH=$PATH:/home/linux/XXX/bin

7、shell语句

​	 1）、解释性语句

​		   #表示注释一行，//不行的
​           #!  告诉编译器使用的解析脚本的shell种类		
​           注意：与c语言不同的是单行注释//和多行注释/**/都在脚本中不能使用
​		    但是条件注释可以在shell脚本中使用
​				  #if  0
​                  #endif   		   
​		   shell脚本常见注释方式：  单行#  多行条件注释

​	2）、功能性语句

 read    从终端得到一个字符串，如果没有得到会一直处于阻塞（一直等待你输入）的方式read -p “please input a number：” VAL会在终端提示一句话等待输入。read VAL1 VAL2 VAL3  可以从终端同时获得多个变量的值如果你输入的超过3个这个时候多于出来的都会赋值给最后一个VAL3

expr  简单的算术运算  +  -  \*  /  %

test测试语句字符串的比较，字符串的长度，字符串的内容

s1 = s2 	测试两个字符串的内容是否完全一样

s1 != s2	测试两个字符串的内容是否有差异

-z s1 	测试s1 字符串的长度是否为0

-n s1 	测试s1 字符串的长度是否不为0

​	数字的比较，比较数字之间的大小关系

a -eq b 		测试a 与b 是否相等

a -ne b		测试a 与b 是否不相等

a -gt b 		测试a 是否大于b

a -ge b 		测试a 是否大于等于b

a -lt b 		测试a 是否小于b

a -le b 		测试a 是否小于等于b

​	测试文件

-d name      测试name 是否为一个目录
-e name      测试一个文件是否存在
-f name 	  测试name 是否为普通文件
-L name	    测试name 是否为符号链接
-r name 	    测试name 文件是否存在且为可读
-w name 	  测试name 文件是否存在且为可写
-x name 	  测试name 文件是否存在且为可执行
-s name 	  测试name 文件是否存在且其长度不为0
f1 -nt f2 	  测试文件f1 是否比文件f2 更新
f1 -ot f2 	  测试文件f1 是否比文件f2 更旧

​	3）控制性语句

if语句

if 条件表		（ if [ 条件表1 -o 条件表2 ]）
then  命令表
elif 条件表
then 
命令表
fi

switch case 语句

case  条件表 in       //条件表是一个变量
	模式1 | 模式2）    可以多个模式组合，|条件表
				 ;;
	模式3）
			 条件表
				 ;;
esac

for循环

for 变量  in  单词表
do
          命令表	
done

while循环

while  条件表	
do	
           命令表
done	

​	4）、shell中的函数

 定义方式一：
		   fun()
             {
			    函数体
			 }
定义方式二：
           function fun()
             {
			      函数体
			 }           
 调用
              fun
传参：    //作用域只对函数体有效
                fun 3 4  
                3对应 $1
                4对应 $2				

## 4.21、gcc编译和gdb调试

###  1、gun工具

编译工具：把一个源程序编译为一个可执行程序（gcc）

调试工具：能对执行程序进行源码或汇编级调试（gdb）

软件工程工具：用于协助多人开发或大型软件项目的管理，如make、CVS、Subvision

其他工具：用于把多个目标文件链接成可执行文件的链接器，或者用作格式转换的工具。

### 2、gcc编译器

​	全称为GNU CC ，GNU项目中符合ANSI C标准的编译系统   编译如C、C++、Object C、Java、Fortran、Pascal、Modula-3和Ada等多种语言GCC是可以在多种硬体平台上编译出可执行程序的超级编译器，其执行效率与一般的编译器相比平均效率要高20%~30%3、编译器的组成

### 3、编译器的组成

​		分析器：分析器将源语言程序代码转换为汇编语言。因为要从一种格式转换为另一种格式（C到汇编），所以分析器需要知道目标机器的汇编语言。汇编器：汇编器将汇编语言代码转换为CPU可以执行字节码（指令集）。

​      链接器：链接器将汇编器生成的单独的目标文件组合成可执行的应用程序。链接器需要知道这种目标格式以便工作。

​      标准C库：核心的C函数都有一个主要的C库来提供。如果在应用程序中用到了C库中的函数，这个库就会通过链接器和源代码连接来生成最终的可执行程序。

### 4、gcc编译的过程

 gcc hello.c -o hello
		a.out 或者 hello
		1）、预处理
		     头文件的展开、宏的替换、去注释
			 gcc -E hello.c -o hello.i
		2）、编译
		     语法、词法进行检查,最后生成了汇编代码
			 gcc -S hello.i -o hello.s
		3）、汇编
		     生成二进制文件
			 gcc -c hello.s -o hello.o
		4）、链接
		     链接到库，如果你使用了printf这个函数，链接到标准C库
			 gcc hello.o -o hello