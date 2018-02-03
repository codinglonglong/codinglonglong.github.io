.. title: Redis修改默认端口
.. slug: redisxiu-gai-mo-ren-duan-kou
.. date: 2017-12-30 23:31:05 UTC+08:00
.. tags: redis
.. category: Linux
.. link: 
.. description: 
.. type: text


::

    >> emacs /etc/redis/redis.conf
    port 8083
    bind 0.0.0.0
    >> redis-server /etc/redis/redis.conf

    