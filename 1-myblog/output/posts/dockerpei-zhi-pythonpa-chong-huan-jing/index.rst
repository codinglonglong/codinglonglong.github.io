.. title: Docker配置Python爬虫环境
.. slug: dockerpei-zhi-pythonpa-chong-huan-jing
.. date: 2017-02-28 22:29:02 UTC+08:00
.. tags: Docker, Python, WebCrawler
.. category: Python
.. link: 
.. description: 
.. type: text

1、新建容器。

    ::

        >> docker run --name webcrawler -i -t -p 8080:8080 -v ~/share/:/usr/development/ ubuntu:14.04 /bin/bash

2、修改软件源。

    ::

        >> vi /etc/apt/sources.list
        :%s/archive.ubuntu/cn.archive.ubuntu/g
        :wq

3、更新软件。

    ::

        >> apt update

4、安装必要的软件和第三方库。

    ::

        >> apt install python
        >> apt install python-pip
        >> apt install python-dev
        >> pip install beautifulsoup4
        >> apt install libdecodeqr-dev libopencv-dev
        >> pip install pydecodeqr
        >> apt install libcurl4-openssl-dev
        >> pip install -U setuptools pip
        >> apt install libxml2-dev libxslt-dev libssl-dev
        >> pip install grab
        >> pip install robobrowser
        >> pip install pycurl
        >> pip install splinter
        >> pip install qrcode
        >> pip install requests

**参考**

http://www.python-requests.org/en/master/

https://www.crummy.com/software/BeautifulSoup/bs4/doc/index.html#

https://github.com/six519/pydecodeqr

https://github.com/lincolnloop/python-qrcode

http://pycurl.io/docs/latest/index.html

http://docs.grablib.org/en/latest/

http://robobrowser.readthedocs.io/en/latest/

http://splinter.readthedocs.io/en/latest/index.html





