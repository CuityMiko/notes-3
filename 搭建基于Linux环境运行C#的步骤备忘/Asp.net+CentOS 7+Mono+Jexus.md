## C#/ASP.NET跨平台测试一 （Asp.net+CentOS 7+Mono+Jexus）    
能够运行VS2015创建的MVC Web程序

###1 软件、环境
* 1.1 VMware
* 1.2 CentOS-7-x86_64-Everything-1503-01.iso
* 1.3 Mono-4.2.2.10.tar.bz2
* 1.4 Jexus-5.6.5
    
 
###2 步骤

* 2.1 更新系统：yum -y update
    
*  2.2 安装Mono需要的关联库
	* yum -y install gcc gcc-c++ bison pkgconfig glib2-devel gettext make libpng-devel libjpeg-devel libtiff-devel libexif-devel giflib-devel libX11-devel freetype-devel fontconfig-devel  cairo-devel
	* yum –y install build-essential automake autoconf libtool bison libglib2.0-dev libfreetype6-dev libfontconfig-dev gettext libgif-dev libtiff4-dev libpng12-dev libexif-dev libx11-dev libxft-dev libjpeg-dev
          
*  2.3 安装Mono需要的GDI+兼容API库Libgdiplus：libgdiplus-3.12  
          下载地址：http://download.mono-project.com/sources/libgdiplus/
    
* 2.4 安装mono：mono-4.2.1.60      
	* tar zxvf mono-4.2.1.60.tar.gz
	* cd mono-4.2.1.60
 	* ./confingure --prefix=/usr
 	* make && make install     
 	
          下载地址：http://download.mono-project.com/sources/mono/     
          
          输入 mono -V，如有Mono版本信息,则安装成功；安装Mono后，运行ldconfig命令一次
    
*  2.5 安装Jexus：jexus-5.6.5        
          下载地址：http://www.jexus.org/，更详细配置请参见官网
          
          >>设置Jexus服务开机自启动：
            方案一：在/etc/rc.local文件的加入“/usr/jexus/jws start”一行。注意，路径应该是你系统中JWS的实际路径，不要把路径写错了。
                    修改该文件权限并重启：chmod +x /etc/rc.d/rc.local
            方案二：参见http://www.cnblogs.com/Zendic/p/3862325.html最后一行内容
          
          命令参数与对应的功效：
           jws start          	  : 启动Jexus；
           jws start 网站名    	: 启动指定的网站
           jws restart            : 重启Jexus
           jws restart 网站名      : 重启指定的网站
           jws stop               : 停止Jexus
           jws stop 网站名         : 停止指定的网站
           jws regsvr             : 注册jexus所需要的全局程序集（本命令只在安装或更新jexus后才用，而且必须用一次）。
           jws status             : Jexus是否在运行中
           jws -v                 : 显示Jexus的版本号
          
* 2.6 安装Jexus完成后，添加80端口到白名单中（最好关闭防火墙）     
       * 添加：sbin/iptables -I INPUT -p tcp --dport 80 -j ACCEPT 
       * 保存：iptables-save  
        //低版本使用 /etc/rc.d/init.d/iptables save 保存     
        或者
       * 停止firewall （CentOS 7防火墙命令）： systemctl stop firewalld.service
       * 禁止firewall开机启动：systemctl disable firewalld.service
 
###3 其他
* 以上所有的安装都用root身份；
* Mono、Libgdiplus等安装的路径请固定为：--prefix=/usr。因为jexus默认会安装到/usr/jexus/，它需要使用到Mono的一个库。
* Jexus全新安装，请首先建立一个默认的网站文件夹:/var/www/default
* Jexus需要设置自启动
  
  
  
###4 参考资料
http://www.cnblogs.com/shanyou/archive/2012/01/07/2315982.html      
http://www.cnblogs.com/acles/archive/2013/09/11/3313716.html      
http://www.cnblogs.com/Zendic/p/3862325.html（详细讲解高低版本的命令区别+添加为系统服务随机启动设置讲解）      
http://www.cnblogs.com/wander1129/archive/2011/12/16/mono.html      
http://www.51mono.com/Article/Show/45       
http://www.cnblogs.com/shanyou/archive/2013/05/04/3060181.html

  
        
