һ��ubuntu12.04����OpenJdk7�Ĺ��̣�
---------------------------


> 1����װgcc��g++��make��
> sudo apt-get install build-essential
> 
> 2����װant1.7����
> sudo apt-get install ant
> 
> 3����װXRender
> sudo apt-get install libxrender-dev
> sudo apt-get install xorg-dev
> 
> 4����װalsa
> sudo apt-get install libasound2-dev
> 
> 5����װCups
> sudo apt-get install libcups-dev
> 
> 6����װjdk6
> 
> 7������
> sudo apt-get install gawk zip libxtst-dev libxi-dev libxt-dev
> 
> 8����������ű�
> \#����ѡ��
> export LANG=C
\#Bootstrap JDK�İ�װ·��
> export ALT_BOOTDIR=/home/hadoop/softwares/jdk1.6.0_45
> \#�����Զ�����
> export ALLOW_DOWNLOADS=true
> \#���б�����߳���������Ϊ��CPU�ں�����һ�¼���
> export HOTSPOT_BUILD_JOBS=4
> export ALT_PARALLEL_COMPILE_JOBS=4
> \#�Ƚϱ���build�����ľ�������ǰ�汾�Ĳ���
> export SKIP_COMPARE_IMAGES=true
> \#ʹ��Ԥ����ͷ�ļ�����������
> export USE_PRECOMPILED_HEADER=true
> \#Ҫ���������
> export BUILD_LANGTOOLS=true
> \#export BUILD_JAXP=false
> \#export BUILD_JAXWS=false
> \#export BUILD_CORBA=false
> export BUILD_HOTSPOT=true
> export BUILD_JDK=true
> \#Ҫ����İ汾
> \#export SKIP_DEBUG_BUILD=false
> \#export SKIP_FASTDEBUG_BUILD=false
> \#export DEBUG_NAME=debug
> \#����Ϊfalse���Աܿ�javaws�������Java���֮��Ĳ��ֵ�build
> BUILD_DEPLOY=false
> \#����Ϊfalse�Ͳ���build����װ��
> BUILD_INSTALL=false
> \#�������Ĵ��·��
> export ALT_OUTPUTDIR=/home/hadoop/myjdk
> \#������������������ȥ��
> unset JAVA_HOME
> unset CLASSPATH
> \#����
> make 2 > &1 | tee $ALT_OUTPUTDIR/build.log
> 
> 9���������֮�󣬽����������j2sdk-imageĿ¼��
> ִ��bin/java -version
> 

�������ܳ��ֵ����⣺
----------

   
> 1��time is more than 10 years from present
> �޸�jdk/src/share/classes/java/util/CurrencyData.properties�е� TR=TRL;2004-12-31-22-00-00;TRYΪ TR=TRL;2014-12-31-22-00-00;TRY
> 
> 2��__LEAF redifined
> ʹ��patches/7103224.patch�޸�bug
> 
> 3��ERROR: You do not have access to valid Cups header files.
> sudo apt-get install libcups2-dev
> 
> 4��ERROR: echo "*** This OS is not supported:" 'uname -a'; exit 1;
> ע��hostspot/make/linux/Makefile�����checkOS
> check_os_version:
> \#ifeq (\$(DISABLE_HOTSPOT_OS_VERSION_CHECK)\$(EMPTY_IF_NOT_SUPPORTED),)
> \# $(QUIETLY) >&2 echo "*** This OS is not supported:" `uname -a`; exit 1;
> \#endif
> 
> 5��ERROR undefined reference to 'snd_pcm_format_**
> ʹ��patches/7100369.patch�޸�bug
> 
> 6��ʹ��jdk1.6��ΪBootstrap JDK����JDK1.7���ܻ��������
> 

�����ο�����
------
 
   
> 1�����������Java�������
   
> 2��http://cduym.iteye.com/blog/1892416