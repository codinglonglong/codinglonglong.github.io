.. title: vuejs学习(7)
.. slug: vuejsxue-xi-7
.. date: 2017-01-13 20:28:47 UTC+08:00
.. tags: vuejs, javascript, vue-cli
.. category: javascript
.. link: 
.. description: 
.. type: text

本文对比两种条件渲染， **v-if** 和 **v-show** 。

测试代码TodoItem.vue如下：

    .. code-block:: html
        :number-lines:

        <template>
        <div id="todoitem">
            <div v-if="flag">你好</div>
            <div v-show="flag">你好</div>
            <div v-if="flag1">你好</div>
            <div v-show="flag1">你好</div>
        </div>
        </template>

        <script>
        export default {
            data: function () {
                return {
                    flag: true,
                    flag1: false,
                }
            },
        }
        </script>

        <style scoped>
        </style>

很明显，输出结果是两行“你好”。貌似v-if和v-show没什么区别，这里需要注意：

**v-if 有更高的切换消耗而 v-show 有更高的初始渲染消耗。因此，如果需要频繁切换使用的话， v-show 较好，而如果在运行时条件不大可能发生改变，则使用 v-if 较好。**
