.. title: Ubuntu14.04上安装JDK
.. slug: ubuntu1404shang-an-zhuang-jdk
.. date: 2015-09-07 19:22:07 UTC+08:00
.. tags: Ubuntu, java
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

1、访问 http://www.oracle.com/technetwork/java/javase/downloads/index.html ，
下载Java Platform (JDK)。

选择Linux x64	165.17 MB  	jdk-8u40-linux-x64.tar.gz

2、解压
::
   
   >> tar -zxvf jdk-8u40-linux-x64.tar.gz

3、新建目录
::

   >> cd /usr/lib
   >> sudo mkdir jvm
   >> cd jvm

4、把解压好的文件夹放入jvm目录
::

   >> sudo mv ~/Downloads/jdk1.8.0_40 .

5、修改环境变量
::
   
   >> gedit ~/.bashrc

添加如下内容：
::
   
   export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_40
   export JRE_HOME=${JAVA_HOME}/jre   
   export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib   
   export PATH=${JAVA_HOME}/bin:$PATH 

::
      
   >> source ~/.bashrc

6、更新命令配置
::

   >> sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.8.0_40/bin/java 300
   >> sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.8.0_40/bin/javac 300
   >> sudo update-alternatives --config java
   >> sudo update-alternatives --config javac

7、查看版本
::

   >> java -version
   >> javac -version
