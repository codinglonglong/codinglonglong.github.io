.. title: ZeroMQ的三种基本通信模型
.. slug: zeromqde-san-chong-ji-ben-tong-xin-mo-xing
.. date: 2017-05-17 22:26:54 UTC+08:00
.. tags: ZeroMQ, Python
.. category: Python
.. link: 
.. description: 
.. type: text


**安装ZeroMQ的Python支持**

    .. code-block:: bash

        apt install python3-pip
        pip3 install pip --upgrade -i http://pypi.doubanio.com/simple/ 
        pip3 install pyzmq -i http://pypi.doubanio.com/simple/ 


**第一种模型：“请求-回复”模型**


服务端：

    .. code-block:: python
        :number-lines:

        import zmq
        import time
        context = zmq.Context()
        socket = context.socket(zmq.REP)
        socket.bind("tcp://*:5555")
        while True:
            message = socket.recv_string()
            print("receive request: ", message)
            time.sleep(1)
            reply = "World"
            socket.send_string(reply)
            print("send reply: ", reply)


客户端：

    .. code-block:: python
        :number-lines:

        import zmq
        context = zmq.Context()
        socket = context.socket(zmq.REQ)
        socket.connect("tcp://172.16.0.111:5555")
        for request in range(1, 10):
            print("send request: ", request)
            socket.send_string("Hello")
            message = socket.recv_string()
            print("receive reply: ",  message)


**第二种模型：“发布-订阅”模型**


服务端：

    .. code-block:: python
        :number-lines:

        import zmq
        import time
        from zmq.utils.strtypes import asbytes
        context = zmq.Context()
        socket = context.socket(zmq.PUB)
        socket.bind("tcp://*:5000")
        topics = [b"a", b"b"]
        while True:  
            msg = "Hello, a"
            socket.send_multipart([topics[0], asbytes(msg)])
            time.sleep(0.1)
            msg = "Hello, b"
            socket.send_multipart([topics[1], asbytes(msg)])
            time.sleep(0.5)




客户端：

    .. code-block:: python
        :number-lines:

        import time
        import zmq
        context = zmq.Context()
        socket = context.socket(zmq.SUB)
        socket.connect("tcp://172.16.0.111:5000") 
        socket.setsockopt_string(zmq.SUBSCRIBE, "a") 
        while True:  
            topic, msg = socket.recv_multipart()
            print(topic)
            print(msg)



**第三种模型：“平行管道”模型**


服务端：

    .. code-block:: python
        :number-lines:

        import zmq
        import random
        import time
        context = zmq.Context()
        sender = context.socket(zmq.PUSH)
        sender.bind("tcp://*:5000")
        sink = context.socket(zmq.PUSH)
        sink.connect("tcp://172.16.0.113:5001")
        print("Press Any Key to Start")
        _ = input()
        sink.send_string("0")
        totalsec = 0
        for task in range(100):
            workload = random.randint(1, 100)
            totalsec = totalsec + workload
            sender.send_string(str(workload))
        print("Total Expected Time: " + str(totalsec) + "s.")


执行端：

    .. code-block:: python
        :number-lines:

        import sys
        import time
        import zmq
        context = zmq.Context()
        receiver = context.socket(zmq.PULL)
        receiver.connect("tcp://172.16.0.111:5000")
        sender = context.socket(zmq.PUSH)
        sender.connect("tcp://172.16.0.113:5001")
        while True:
            s = receiver.recv_string()
            time.sleep(int(s)*0.001)
            sender.send_string("")




汇总端：

    .. code-block:: python
        :number-lines:

        import sys
        import time
        import zmq
        context = zmq.Context()
        receiver = context.socket(zmq.PULL)
        receiver.bind("tcp://*:5001")
        s = receiver.recv_string()
        print(s)
        start = time.time()
        for task in range(100):
            s = receiver.recv_string()
        end = time.time()
        print("Total Elapsed Time: " + str((end-start)*1000) + "s.")


运行结果：


.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/zeromq_worker.png


**总结**

1. “请求-回复”模型就好比两个人聊天。

2. “发布-订阅”模型就好比听FM。

3. “平行管道”模型就好比MapReduce。

