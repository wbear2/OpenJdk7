一、ubuntu12.04编译OpenJdk7的过程：
---------------------------

   > 
1、安装gcc、g++、make等
   > sudo apt-get install build-essential
   > 
2、安装ant1.7以上
   > sudo apt-get install ant
   > 
3、安装XRender
   > sudo apt-get install libxrender-dev
   > sudo apt-get install xorg-dev
   > 
4、安装alsa
   > sudo apt-get install libasound2-dev
   > 
5、安装Cups
   > sudo apt-get install libcups-dev
   > 
6、安装jdk6
   > 
7、其它
   > sudo apt-get install gawk zip libxtst-dev libxi-dev libxt-dev
   > 
8、构建编译脚本
    > 
9、编译完成之后，进入编译结果的j2sdk-image目录中
   > 执行bin/java -version
   > 

二、可能出现的问题：
----------

   > 
1、time is more than 10 years from present
   > 修改 jdk/src/share/classes/java/util/CurrencyData.properties中的 TR=TRL;2004-12-31-22-00-00;TRY为 TR=TRL;2014-12-31-22-00-00;TRY
   > 
2、__LEAF redifined
   > 使用patches/7103224.patch修复bug
   > 
3、ERROR: You do not have access to valid Cups header files.
   > sudo apt-get install libcups2-dev
   > 
4、ERROR: echo "*** This OS is not supported:" 'uname -a'; exit 1;
   > 注释hostspot/make/linux/Makefile里面的checkOS
   > 
5、ERROR undefined reference to 'snd_pcm_format_**
   > 使用patches/7100369.patch修复bug
   > 
6、使用jdk1.6作为Bootstrap JDK，用JDK1.7可能会出现问题
   > 

三、参考资料
------
> 
   
> 1、《深入理解Java虚拟机》
   
> 2、http://cduym.iteye.com/blog/1892416

