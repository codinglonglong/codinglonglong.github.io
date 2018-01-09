.. title: pexpect执行无错误，也无结果
.. slug: pexpectzhi-xing-wu-cuo-wu-ye-wu-jie-guo
.. date: 2018-01-01 10:38:12 UTC+08:00
.. tags: Python, pexpect, Linux
.. category: Python
.. link: 
.. description: 
.. type: text


最后一行代码可以解决这个问题。

.. code-block:: python
    :number-lines:

    import pexpect

    userid = 1
    userpass = "abcdef"
    username = "写程序的龙龙"
    useremail = "codinglonglong@126.com"

    child = pexpect.spawn('ssh-keygen -t rsa -C "' + useremail + '"')
    print("1")
    child.expect(": ")
    child.sendline("/home/long/.ssh/u" + str(userid))
    print("2")
    child.expect(": ")
    child.sendline(str(userpass))
    print("3")
    child.expect(": ")
    child.sendline(str(userpass))
    child.expect(pexpect.EOF)


