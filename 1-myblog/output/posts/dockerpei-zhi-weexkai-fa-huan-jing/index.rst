.. title: Docker配置weex开发环境
.. slug: dockerpei-zhi-weexkai-fa-huan-jing
.. date: 2017-03-13 22:30:01 UTC+08:00
.. tags: Docker, weex, vuejs
.. category: javascript
.. link: 
.. description: 
.. type: text

1、安装weex。

    ::

        >> npm install -g cnpm --registry=https://registry.npm.taobao.org
        >> cnpm install -g weex-toolkit

2、初始化weex项目。

    ::

        >> weex init testapp

3、构建并测试项目。

    ::

        >> cd testapp
        >> npm install
        >> npm run dev
        >> npm run serve

4、主系统访问 http://192.168.99.100:8080/ 即可，这里只是实现浏览器预览，后面我们再进一步研究打包apk。



