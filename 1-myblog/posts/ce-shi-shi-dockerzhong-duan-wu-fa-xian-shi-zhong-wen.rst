.. title: 测试时，Docker终端无法显示中文
.. slug: ce-shi-shi-dockerzhong-duan-wu-fa-xian-shi-zhong-wen
.. date: 2017-12-31 00:00:02 UTC+08:00
.. tags: redis, Docker
.. category: Linux
.. link: 
.. description: 
.. type: text


测试代码的时候，无法用print在Docker终端输出中文，对于这个问题，我们采用的办法是将要输出的信息记录在redis里，然后在主系统通过redis图形客户端查看，这样的好处在于:

1. 不需要改动docker镜像本身；
2. redis可以很好地支持中文；
3. 测试过程可记录，容易追溯问题所在。


 


