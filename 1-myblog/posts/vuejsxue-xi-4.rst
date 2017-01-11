.. title: vuejs学习(4)
.. slug: vuejsxue-xi-4
.. date: 2017-01-11 21:20:13 UTC+08:00
.. tags: vuejs, javascript, vue-cli
.. category: javascript
.. link: 
.. description: 
.. type: text

本文初步学习一下引入外部库函数的方法，我们接着文章 https://codinglonglong.github.io/posts/vuejsxue-xi-3/ 的代码做。

我们修改 TodoList.vue 文件，代码如下：

    .. code-block:: html
        :number-lines:

        <template>
        <div id="todolist">
            <ul>
                <TodoItem v-for="item in getrange(1, 10, 2)" v-bind:todomessage="addhead(item)"></TodoItem>
            </ul>
        </div>
        </template>

        <script>
        import TodoItem from './components/TodoItem'
        import _ from 'lodash'

        export default {
            methods: {
                getrange: function (start, end, step) {
                    return _.range(start, end, step);
                },
                addhead: function (tempstr) {
                    return "容器" + tempstr;
                }
            },
            components: {
                TodoItem
            }
        }
        </script>

        <style scoped>
        li{
            color: blue;
        }
        </style>

在上述的代码中，我们需要学到以下几个问题：

1. v-for指令中in的后面可以是一个函数。
2. v-bind指令可以绑定子组件中props涉及到的变量。
3. 绑定的变量可以进行进一步的计算，也就是计算属性。
4. 想引入外部库函数时，可以先用内部函数封装一下，就可以在template中使用了。
5. lodash提供了很多js内置库中没有的工具函数。
