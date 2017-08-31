.. title: 基于mqtt的消息推送
.. slug: ji-yu-mqttde-xiao-xi-tui-song
.. date: 2017-05-21 14:59:56 UTC+08:00
.. tags: mqtt, Python, Linux, mosquitto, Android
.. category: Linux
.. link: 
.. description: 
.. type: text


**t1上**

1、安装mosquitto服务器。

    .. code-block:: bash

        >> apt install wget
        >> wget http://mosquitto.org/files/source/mosquitto-1.4.11.tar.gz
        >> tar zxvf mosquitto-1.4.11.tar.gz
        >> cd mosquitto-1.4.11
        >> apt install libc-ares-dev uuid-dev libwebsockets-dev libssl-dev 
        >> make binary
        >> make install
        >> vi /etc/profile
        export PATH=/usr/local/bin:$PATH
        >> source /etc/profile
        >> useradd -m mosquitto


2、启动mosquitto服务。

    .. code-block:: bash

        >> mosquitto


**t2上**

1、安装mosquitto的Python客户端。

    .. code-block:: bash

        >> pip3 install paho-mqtt


2、编写并启动消息接收端。

    .. code-block:: python
        :number-lines:

        import paho.mqtt.client as mqtt
        import json

        def on_connect(client, userdata, flags, rc):
            client.subscribe("test")

        def on_message(client, userdata, msg):
            print(msg.topic + " " + str(msg.payload))

        client = mqtt.Client()
        client.on_connect = on_connect
        client.on_message = on_message
        try:
            client.connect("172.16.0.111", port=1883)
            client.loop_forever()
        except KeyboardInterrupt:
            client.disconnect()

**t3上**

1、安装mosquitto的Python客户端。

    .. code-block:: bash

        >> pip3 install paho-mqtt


2、编写并启动消息发送端。

    .. code-block:: python
        :number-lines:

        import paho.mqtt.publish as publish
        host = "172.16.0.111"
        topic = "test"
        payload = "hi"
        publish.single(topic, payload, qos=1, hostname=host)


还可以这样写

    .. code-block:: python
        :number-lines:

        import paho.mqtt.client as mqtt
        import time
        client = mqtt.Client()
        client.connect("172.16.0.111")
        topic = "test"
        payload = "hi"
        for i in range(10):
            client.publish(topic, payload)
            time.sleep(1)


**注意**

要先启动消息接收端，再启动消息发送端。如果分别在两个主机上启动消息接收端和消息发送端，那么就可以实现即时通讯了。



