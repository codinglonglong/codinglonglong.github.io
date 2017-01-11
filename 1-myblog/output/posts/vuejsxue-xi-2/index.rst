.. title: vuejs学习(2)
.. slug: vuejsxue-xi-2
.. date: 2017-01-11 14:46:11 UTC+08:00
.. tags: vuejs, javascript, vue-cli
.. category: javascript
.. link: 
.. description: 
.. type: text

本文初步学习一下vuejs提供的基本指令v-model、v-on:click、v-bind:title、v-if和v-for。

在文章 https://codinglonglong.github.io/posts/vuejsxue-xi-1/ 的基础上，我们修改了App.vue，代码如下。

    .. code-block:: html
        :number-lines:

        <template>
        <div id="myapp">
            <input v-model="name">
            <p>Hello, {{name}}</p>
            <button v-on:click="sayhello" v-bind:title="tooltip">sayhello</button>
            <div class="message">
                <button v-on:click="toggleshow">切换显示</button>
                <span class="content" v-if="flag">一条消息</span>
            </div>
            <select>
                <option v-for="week in weeks">{{week}}</option>
            </select>
        </div>
        </template>

        <script>
        export default {
            data: function () {
                return {
                    name: "龙龙龙",
                    tooltip: "点击我问好...",
                    flag: true,
                    weeks: ["星期一", "星期二", "星期三", "星期四", "星期五", "星期六", "星期日"],
                }
            },
            methods: {
                sayhello: function () {
                    alert(this.name);
                },
                toggleshow: function(){
                    if(this.flag){
                        this.flag = false;
                    }else{
                        this.flag = true;
                    }
                }
            }
        }
        </script>

        <style>
        p {
            font-size: 30px;
            color: blue;
        }
        .message {
            display: block;
            width: 100px;
            margin-top: 50px;
        }
        .content{
            color: green;
        }
        </style>


通过这段代码，可以看出：

1. v-model 用来通过输入控件同步消息的显示。
2. v-on:click 用来设定鼠标单击事件，事件函数定义在methods里。
3. v-bind:title 用来设定鼠标放在某元素上显示的信息。
4. v-if 用来根据某一变量的值决定元素的显示与否。
5. v-for 用来绑定一系列数据。

vuejs提供的类似指令还有很多，我们后面接着学习。