.. title: vuejs学习(6)
.. slug: vuejsxue-xi-6
.. date: 2017-01-13 08:45:45 UTC+08:00
.. tags: vuejs, javascript, vue-cli
.. category: javascript
.. link: 
.. description: 
.. type: text

本文进一步学习条件渲染。

我们修改了TodoItem.vue文件，代码如下：

    .. code-block:: html
        :number-lines:

        <template>
            <div id="todoitem">
                <div v-if="flag===1">星期一</div>
                <div v-else-if="flag===2">星期二</div>
                <div v-else-if="flag===3">星期三</div>
                <div v-else-if="flag===4">星期四</div>
                <div v-else-if="flag===5">星期五</div>
                <div v-else-if="flag===6">星期六</div>
                <div v-else-if="flag===7">星期日</div>
                <div v-else>参数错误</div>
            </div>
        </template>
        <script>
            export default {
                data: function () {
                    return {
                        flag: 6,
                    }
                },
            }
        </script>

        <style scoped>
        </style>

在上述的代码中，我们需要学到以下几个问题：

1. 可以实现多分支渲染。
2. 注意js中==和===的区别，我想这个问题可以单独写篇文章了……