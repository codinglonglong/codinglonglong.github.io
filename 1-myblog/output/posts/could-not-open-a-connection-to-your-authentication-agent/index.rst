.. title: Could not open a connection to your authentication agent
.. slug: could-not-open-a-connection-to-your-authentication-agent
.. date: 2017-01-09 22:11:08 UTC+08:00
.. tags: git
.. category: git 
.. link: 
.. description: 
.. type: text

在执行ssh-add时，如果出现“Could not open a connection to your authentication agent”这一错误信息，可以通过如下方法解决：

.. code-block:: bash

    >> eval `ssh-agent`

**注意** 是 **\`** 而不是 **\'** 。