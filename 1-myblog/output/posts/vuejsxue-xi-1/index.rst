.. title: vuejs学习(1)
.. slug: vuejsxue-xi-1
.. date: 2017-01-10 09:06:42 UTC+08:00
.. tags: vuejs, javascript, vue-cli
.. category: javascript
.. link: 
.. description: 
.. type: text

本文初步学习如何使用vue-cli建立一个简单的网页组件。

1. 参考 https://cn.vuejs.org/v2/guide/installation.html 安装好vue和vue-cli。

2. 用vue创建一个简单的项目，删除已有src目录中的文件。

3. 找到index.html如下，不用改动。

    .. code-block:: html
        :number-lines:

        <!DOCTYPE html>
        <html>
        <head>
            <meta charset="utf-8">
            <title>test</title>
        </head>
        <body>
            <div id="app"></div>
            <!-- built files will be auto injected -->
        </body>
        </html>
    
   这里应该留意到已经包含一个id是app的div，未来要写的代码经过编译之后，会放在这个div的位置，而 <div id="app"></div> 会被替换掉。

4. 在src目录下新建main.js，这是整个网站代码的入口，如下。

    .. code-block:: html
        :number-lines:

        import Vue from 'vue'
        import App from './App'

        new Vue({
            el: '#app',
            template: '<App/>',
            components: { App }
        })

   这里应该注意到，el，也就是element，绑定的是前面index.html中的 <div id="app"></div> ，而该位置对应的模板则是来自名为App的组件，也就是将App组件渲染到id为app的div的位置上。

5. 在src目录下新建App.vue，这是网站的一个组件，可以多次反复使用，代码如下。

    .. code-block:: html
        :number-lines:

        <template>
            <div id="myapp">
                <p>Hello, {{Name}}</p>
                <button v-on:click="sayhello">sayhello</button>
            </div>
        </template>

        <script>
        export default {
            data: function () {
                return {
                    Name: "龙龙龙"
                }
            },
            methods: {
                sayhello: function () {
                    alert(this.Name);
                }
            }
        }
        </script>

        <style>
        p {
            font-size: 30px;
            color: blue;
        }
        </style>


   通过这段代码，可以看出：

   1. 一个vue组件由三大部分组成，<template></template>（组件模板），<script></script>（组件脚本），<style></style>（组件样式）。
   2. 组件样式部分就是最基本的CSS。
   3. 组件脚本部分被export default{}包围，这个例子中给出了data（数据）和methods（方法），可以学到如何绑定数据和如何添加自定义函数。
   4. 组件模板部分必须被一个根div包围，在本例中是 <div id="myapp"></div>。
   5. 按钮点击事件的实现采用 <button v-on:click="sayhello">sayhello</button>。

**总结**

这个简单的例子一共涉及了以下几个问题：

1. vue组件的基本格式；
2. 如何加样式；
3. 如何加自定义函数；
4. 如何做数据绑定；
5. 如何把组件和网页联系在一起。

后面我们将继续尝试多个组件的网站怎么写。
