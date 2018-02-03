.. title: 使用pexpect远程登录SSH
.. slug: shi-yong-pexpectyuan-cheng-deng-lu-ssh
.. date: 2015-09-16 14:55:48 UTC+08:00
.. tags: pexpect, Python
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

pexpect可以自动和命令行程序进行交互，在系统部署和测试的时候非常好用。

以远程登录SSH并执行命令为例
::
   
   >> emacs dparkstarter.py
   import pexpect

   ip = "192.168.1.211"
   name = "long"
   child = pexpect.spawn('ssh  %s@%s' % (name, ip))
   child.expect('$')
   child.sendline('python dparkslave.py')
   child.interact() 
   >> python dparkstarter.py

程序可以自动登录SSH，然后执行python dparkslave.py这条命令。

