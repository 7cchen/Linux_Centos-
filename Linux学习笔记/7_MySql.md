#MySql基础  
##1.安装MySql  
安装MySql：

	# yum 	install	   mysql-server
MySql初始化：

	# service mysqld start		//启动MySql
	# netstat	-tnlp		//查看端口号，注意MySql的端口号是3306
	# mysql_secure_installation		//初始化MySql
	之后：没有密码则直接回车，之后根据要求设置密码；
		 其次再移除匿名用户（Y）；
		 不允许root用户远程登录（Y）；
		 移除测试数据库（N）；
		 重新加载权限表（Y）。
MySql启动：  

	# service mysql start/stop/restart
进入MySql的方式：
	
	# mysql 	-u用户名(root) 	-p
退出MySql到Linux命令行：

	exit  
数据库存储目录：	/var/lib/mysql  
配置文件：	/etc/my.cnf
	
##2.MySql操作  
###数据库操作：  

	show	database;				//显示当前MySql中所有的数据库名
	create	database	数据库名;	 //创建数据库
	drop	database	数据库名; 	 //删除数据库
	use		数据库名;				 //选中使用数据库
###数据表操作：

	show	tables;					//显示当前数据库中所有的表名

	create	table 	表名称（
	列名称		数据类型(长度)[not null /	auto_increment],
	列名称		数据类型(长度),
	列名称		数据类型(长度),
	...,
	primary key(主键字段名)		
	）;								//在当前数据库下创建数据表
	常见的数据类型：int(整形)、char(定长字符)、varchar(不定长字符)。

	desc	表名;						//描述一个数据表（查看表结构）
	drop	table	[if exists]	表明;		//删除一个数据表
###数据库/记录字段操作：  

	增加记录：
	insert	into   	表名称	values(值1，值2...);			//向指定数据表中添加数据
	insert	into	表名称（列1，列2...）	values(值1，值2...);

	查询记录：
	select	列名称1,列名称2...	from	表名称		where	条件;
	select	* 	from 	表名称		where	条件;

	更新记录：
	update	表名称	set		列名称1=新值1，列名称2=新值2...	where	列名称=某值;

	删除记录：
	delete	from	表名称		where	列名称=值;
###备份与还原：
备份：  
	
	全量备份（数据+结构）：
	#	mysqldump	-uroot	-p123456	-A > 	备份文件路径
	
	指定库备份（数据+结构）：
	#	mysqldump	-uroot	-p123456	库名	>	备份文件路径

	多个库备份（数据+结构）：
	#	mysqldump	-uroot	-p123456	--databases	db1	db2	>	备份文件路径
还原（导入）：

	还原全部数据库：	
	（1）mysql命令行：mysql>		source	备份文件路径
	（2）系统命令行：#	mysql -uroot	-p123456	<	备份文件路径

	还原单个数据库（需指定数据库）：
	mysql>		use		数据库名
	mysql>		source 	备份的文件路径

	设置MySql连接字符集：
	mysql>		set		names		utf8;


##3.MySql远程管理工具：
B/S架构：浏览器 / 服务器  

	PMA(phpMyAdmin)
C/S结构：客户端 / 服务器

	navicat、mysqlworkbench
允许MySql远程登录：  
	
	（1）先进入数据库选择mysql数据库；
	（2）执行sql语句：select	host,user	from 	user;
	（3）将其中的一个记录的host值改为“%”，表示可以允许任何地方登录  
	（4）刷新权限表或者重启mysql  
		刷新权限：mysql>		flush	privileges;


##4.扩展：  
1.解压压缩包：

	语法：# tar		-zxvf		*.tar.gz		（大多数）
		 # tar	   	  -jxvf		  *.tar.bz2
	选项：
		-z	通过gzip指令处理文件
		-x	从文件中还原文件
		-v	显示操作过程
		-f	指定一个文件
		-j	支持bzip2解压文件；
2.yum傻瓜式安装：  

	语法：# 	yum		list		//列出当前已经装的和可以装的软件（全部）
		 #	  yum	  search  	名  //搜索指定的关键词的包
		 #	  yum	  [-y]		install		包名		//安装指定的包（-y表示允许）
		 #	  yum	  [-y]		update		[包名]	//更新指定的包，不指定包则更新全部软件
		 #    yum	  [-y]		remove		包名		//卸载指定的包