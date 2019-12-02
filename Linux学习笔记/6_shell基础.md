#Shell基础  
> Shell(外壳)是一个用C语言编写的程序，它是用户使用Linux的基础。Shell既是命令语言，也是程序设计语言。    

##1.Shell介绍
> Shell是指一种应用程序，这个应用程序提供了一个界面，用户通过这个界面访问操作系统内核的服务。  

脚本：  
> 脚本简单来说就是一条条的文字指令，这些文字指令可以看到。  
常见的脚本：JavaScript（前端）、PHP（后端）、Pyhton、Shell等等。  

Linux默认的是Shell是	/bin/bash（重点）。  

###shell入门：  
代码规范：

	#!/bin/bash			【告诉系统当前这个脚本要使用的shell解释器】
	Shell相关指令
文件命名规范：

	文件名.sh
使用流程：

	1.创建.sh文件
	2.编写shell代码
	3.执行shell脚本			【前提：修改权限为可执行：	#chmod +x 路径】
	说明执行shell脚本：	./脚本的路径（tast.sh）		或者		/bin/bash	脚本的路径


##2.shell进阶  
###1.变量  
在一个脚本周期内，其值可以发生改变的量就是变量。   

	变量：先定义再使用。
	定义：变量名=变量的值
	注意：
		1.使用的时候需要在变量名前添加一个“$”
		2.变量名后面的等号左右不能有空格
		3.双引号能够识别变量，并且能够实现转义；单引号不能识别变量，只会原样输出，不能转义。
		4.当在脚本中需要执行一些指令并且执行的结果赋值给变量的时候需要使用反引号（``）
只读变量：  

	语法：readonly	变量名  
接收用户输入：

	语法：read	-p 	提示信息	变量名
删除变量：

	语法：unset	变量名

###2.条件判断语句  

	语法1：	if[condition];then command;fi


	语法2：	if comdition
			  then
			  	command1
				command2
				...
		      else
				command
			  fi


	语法3：	if condition1
			  then
				conmand1
			  elif condition2
			  then
				command2
			  else
				commandN
			  fi

###3.运算符