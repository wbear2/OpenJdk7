一、ubuntu12.04编译OpenJdk7的过程：
---------------------------


> 1、安装gcc、g++、make等
> sudo apt-get install build-essential
> 
> 2、安装ant1.7以上
> sudo apt-get install ant
> 
> 3、安装XRender
> sudo apt-get install libxrender-dev
> sudo apt-get install xorg-dev
> 
> 4、安装alsa
> sudo apt-get install libasound2-dev
> 
> 5、安装Cups
> sudo apt-get install libcups-dev
> 
> 6、安装jdk6
> 
> 7、其它
> sudo apt-get install gawk zip libxtst-dev libxi-dev libxt-dev
> 
> 8、构建编译脚本
> \#语言选项
> export LANG=C
\#Bootstrap JDK的安装路径
> export ALT_BOOTDIR=/home/hadoop/softwares/jdk1.6.0_45
> \#允许自动下载
> export ALLOW_DOWNLOADS=true
> \#并行编译的线程数，设置为和CPU内核数量一致即可
> export HOTSPOT_BUILD_JOBS=4
> export ALT_PARALLEL_COMPILE_JOBS=4
> \#比较本次build出来的镜像与先前版本的差异
> export SKIP_COMPARE_IMAGES=true
> \#使用预编译头文件，编译会更快
> export USE_PRECOMPILED_HEADER=true
> \#要编译的内容
> export BUILD_LANGTOOLS=true
> \#export BUILD_JAXP=false
> \#export BUILD_JAXWS=false
> \#export BUILD_CORBA=false
> export BUILD_HOTSPOT=true
> export BUILD_JDK=true
> \#要编译的版本
> \#export SKIP_DEBUG_BUILD=false
> \#export SKIP_FASTDEBUG_BUILD=false
> \#export DEBUG_NAME=debug
> \#设置为false可以避开javaws和浏览器Java插件之类的部分的build
> BUILD_DEPLOY=false
> \#设置为false就不会build出安装包
> BUILD_INSTALL=false
> \#编译结果的存放路径
> export ALT_OUTPUTDIR=/home/hadoop/myjdk
> \#这两个环境变量必须去掉
> unset JAVA_HOME
> unset CLASSPATH
> \#编译
> make 2 > &1 | tee $ALT_OUTPUTDIR/build.log
> 
> 9、编译完成之后，进入编译结果的j2sdk-image目录中
> 执行bin/java -version
> 

二、可能出现的问题：
----------

   
> 1、time is more than 10 years from present
> 修改jdk/src/share/classes/java/util/CurrencyData.properties中的 TR=TRL;2004-12-31-22-00-00;TRY为 TR=TRL;2014-12-31-22-00-00;TRY
> 
> 2、__LEAF redifined
> 使用patches/7103224.patch修复bug
> 
> 3、ERROR: You do not have access to valid Cups header files.
> sudo apt-get install libcups2-dev
> 
> 4、ERROR: echo "*** This OS is not supported:" 'uname -a'; exit 1;
> 注释hostspot/make/linux/Makefile里面的checkOS
> check_os_version:
> \#ifeq (\$(DISABLE_HOTSPOT_OS_VERSION_CHECK)\$(EMPTY_IF_NOT_SUPPORTED),)
> \# $(QUIETLY) >&2 echo "*** This OS is not supported:" `uname -a`; exit 1;
> \#endif
> 
> 5、ERROR undefined reference to 'snd_pcm_format_**
> 使用patches/7100369.patch修复bug
> 
> 6、使用jdk1.6作为Bootstrap JDK，用JDK1.7可能会出现问题
> 

三、参考资料
------
 
   
> 1、《深入理解Java虚拟机》
   
> 2、http://cduym.iteye.com/blog/1892416