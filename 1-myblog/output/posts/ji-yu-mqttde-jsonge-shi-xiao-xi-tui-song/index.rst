.. title: 基于mqtt的json格式消息推送
.. slug: ji-yu-mqttde-jsonge-shi-xiao-xi-tui-song
.. date: 2017-05-21 18:47:55 UTC+08:00
.. tags: mqtt, Python, Linux, mosquitto, Android
.. category: Linux
.. link: 
.. description: 
.. type: text


基于文章 https://codinglonglong.github.io/posts/ji-yu-mqttde-xiao-xi-tui-song/ ，我们进一步改进测试程序。


**t2上**


编写并启动消息接收端。

    .. code-block:: python
        :number-lines:

        import paho.mqtt.client as mqtt
        import json

        def on_connect(client, userdata, flags, rc):
            client.subscribe("test")

        def on_message(client, userdata, msg):
            print(msg.topic + " " + str(msg.payload))
            message = json.loads(msg.payload.decode("utf-8"))
            print(message["1"])
            print(message["2"])

        client = mqtt.Client()
        client.on_connect = on_connect
        client.on_message = on_message
        try:
            client.connect("172.16.0.111", port=1883)
            client.loop_forever()
        except KeyboardInterrupt:
            client.disconnect()

    
**t3上**


编写并启动消息发送端。

    .. code-block:: python
        :number-lines:

        import paho.mqtt.client as mqtt
        import time
        import json
        client = mqtt.Client()
        client.connect("172.16.0.111")
        topic = "test"
        payload = {1:"hi", 2:"hihi"}
        for i in range(10):
            client.publish(topic, json.dumps(payload))
            time.sleep(1)

