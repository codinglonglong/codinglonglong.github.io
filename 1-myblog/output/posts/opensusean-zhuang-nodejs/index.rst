.. title: openSUSE安装nodejs
.. slug: opensusean-zhuang-nodejs
.. date: 2017-03-28 08:58:42 UTC+08:00
.. tags: openSUSE, nodejs
.. category: Linux
.. link: 
.. description: 
.. type: text

1、下载源码。

    ::
    
        >> wget https://nodejs.org/dist/v6.10.1/node-v6.10.1-linux-x64.tar.gz
        
2、解压。

    ::
    
        >> tar zxvf node-v6.10.1-linux-x64.tar.gz
        
3、链接命令。

    ::
    
        >> sudo ln -s /home/long/software/node/bin/node /usr/local/bin/node
        >> sudo ln -s /home/long/software/node/bin/npm /usr/local/bin/npm
        >> long@linux-iyb2:~> node -v
        v6.10.1
        >> long@linux-iyb2:~> npm -v
        3.10.10

