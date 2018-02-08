.. title: Ubuntu W: GPG error NO_PUBKEY
.. slug: ubuntu-w-gpg-error-no_pubkey
.. date: 2015-09-07 10:44:27 UTC+08:00
.. tags: Ubuntu
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

Ubuntu系统在执行sudo apt-get update之后，可能会出现如下错误：
::

   >> W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

解决办法：
::

   >> gpg --keyserver keyserver.ubuntu.com --recv 16126D3A3E5C1192
   >> gpg --export --armor 16126D3A3E5C1192 | sudo apt-key add -
