##C#/ASP.NET跨平台测试二 （Asp.net+UbuntuOS 14.04+Mono+Jexus）     
能够运行VS2015创建的MVC简单Web程序，success

###1 软件、环境
* 1.1 VMware
* 1.2 ubuntu-14.04.3-server-amd64.iso
* 1.3 Mono-4.2.2.10.tar.bz2
* 1.4 Jexus-5.6.5
    

###2 步骤

* 2.1 安装Mono需要的关联库：   
        apt-get install build-essential automake autoconf libtool bison gettext pkg-config libgdiplus
        
*  2.2 安装Mono：   
	 *   tar jxvf mono-4.2.2.10.tar.bz2     
	 *  cd mono-4.2.2.10     
	 *  ./configure --prefix=/usr     
	 *  make && make install      
          
          下载地址：http://download.mono-project.com/sources/mono/    
          输入 mono -V，如有Mono版本信息,则安装成功；安装Mono后，运行ldconfig命令一次
          
    注：可以使用MoMa工具检查用于开发者使用的MS .net下开发的应用程序迁移到Mono平台的不兼容性检测工具
    
          
*  2.3 安装Jexus：
	 *   tar -zxvf jexus-5.6.5.tar.gz     
	 *   cd jexus-5.6.5    
	 *   ./install
          
          
设置Jexus服务开机自启动：    
            在/etc/rc.local文件的“exit 0”前面，加入“/usr/jexus/jws start”一行。注意，路径应该是你系统中JWS的实际路径，不要把路径写错了。

          
          命令参数与对应的功效：
           jws start           : 启动Jexus；
           jws start 网站名    : 启动指定的网站
           jws restart         : 重启Jexus
           jws restart 网站名  : 重启指定的网站
           jws stop            : 停止Jexus
           jws stop 网站名     : 停止指定的网站
           jws regsvr          : 注册jexus所需要的全局程序集（本命令只在安装或更新jexus后才用，而且必须用一次）。
           jws status          : Jexus是否在运行中
           jws -v              : 显示Jexus的版本号
           
*  2.4 Ubuntu默认没有防火墙，但是账号权限低，先开启root，安装SSH，关闭防火墙(ufw disable)，启动ssh(/etc/init.d/ssh start)
     
###3 其他
* 以上所有的安装都用root身份；
* Mono、Libgdiplus等安装的路径请固定为：--prefix=/usr。因为jexus默认会安装到/usr/jexus/，它需要使用到Mono的一个库。
* Jexus全新安装，请首先建立一个默认的网站文件夹:/var/www/default
* Jexus需要设置自启动
  
###4 参考资料
http://www.cnblogs.com/Zendic/p/3862325.html