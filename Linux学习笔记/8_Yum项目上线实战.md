#Yum项目上线实战（网站运维）  
##1.编译安装与卸载Nginx  
Nginx  
> 是一款比较流行的web服务器软件，类似于Apache。  

安装Nginx  
[https://blog.csdn.net/t8116189520/article/details/81909574](https://blog.csdn.net/t8116189520/article/details/81909574)  

##2.关于LAMP架构
LAMP架构：	Linux	+	Apache		+	MySql	+	PHP  
LNMP架构：	Linux 	+ 	Ngine		+	MySql	+	php-fpm

##3.LAMP环境部署  
1.PHP与Apache的安装  

	#yum	install		php		//自带安装了Apache
	#vim	/etc/httpd/conf/httpd.conf		//把ServerName注释去掉
	#service	httpd	start
	在网页地址栏输入ip地址直接访问（关闭防火墙）

2.MySql的安装与初始化  

	MySql安装：
	#yum	install		mysql-server
	
	初始化操作：
	#service	mysql	start
	#mysql_secure_installation

	测试进行命令行登录：
	#mysql	-uroot -p

	需要远程登录：
	MySql>		use		数据库名;
	MySql>		update		user	set	host='%'	where	host='host名';
	MySql>		flush	privileges;

	阿里云上的安全组放行：允许80和3306端口	

参考：[https://blog.csdn.net/weixin_44487722/article/details/90144252](https://blog.csdn.net/weixin_44487722/article/details/90144252)

3.项目上线

