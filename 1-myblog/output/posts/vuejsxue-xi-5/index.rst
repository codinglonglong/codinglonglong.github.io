.. title: vuejs学习(5)
.. slug: vuejsxue-xi-5
.. date: 2017-01-12 22:05:54 UTC+08:00
.. tags: vuejs, javascript, vue-cli
.. category: javascript
.. link: 
.. description: 
.. type: text

本文初步学习一下样式的动态绑定和计算属性的使用。

我们修改 TodoList.vue 文件，代码如下：

    .. code-block:: html
        :number-lines:

        <template>
        <div id="todolist">
            <TodoItem></TodoItem>
        </div>
        </template>

        <script>
        import TodoItem from './components/TodoItem'

        export default {
            components: {
                TodoItem
            }
        }
        </script>

        <style scoped>

        </style>

可以看出我们把父容器清空了，只添加了一个子容器<TodoItem></TodoItem>。这样做主要是为了保持项目结构，为更复杂的试验做准备。

下面是主角，TodoItem.vue。

    .. code-block:: html
        :number-lines:

        <template>
        <div id="todoitem">
            <button v-on:click="changecolor">更改颜色</button>
            <div class="box" v-bind:class="classObj"></div>
        </div>
        </template>

        <script>
        export default {
            data: function(){
                return{
                    flag: true,
                }
            },
            methods: {
                changecolor: function () {
                    this.flag = !this.flag;
                }
            },
            computed: {
                classObj: function () {
                    return {
                        green: this.flag,
                        blue: !this.flag,
                    }
                }
            }
        }
        </script>

        <style>
        .box {
            display: block;
            width: 100px;
            height: 100px;
            margin: 50px;
        }
        .blue {
            background-color: blue;
        }
        .green {
            background-color: green;
        }
        </style>

在上述的代码中，我们需要学到以下几个问题：

1. class是可以通过v-bind:class绑定的，绑定的目标classObj应该是一个字典结构，并且值是布尔类型，例如{class_a:true, class_b:false}，这就意味着class_a是有效的，class_b是无效的。
2. 可以通过computed引入计算属性。由于classObj函数中存在this.flag，当点击按钮触发changecolor函数修改flag时，会激活computed中的classObj函数，对其返回值进行更新。如果classObj函数中不存在this.flag，那么classObj函数在点击按钮触发changecolor函数时不会被执行，这样实现了高效的基于缓存局部数据更新。而普通的methods在每次调用时都会执行一遍运算，效率会比较低。

上述代码还可以这样写：

    .. code-block:: html
        :number-lines:

        <template>
        <div id="todoitem">
            <button v-on:click="changecolor">更改颜色</button>
            <div v-bind:class="[flag ? 'blue': 'green', 'box’]"></div>
        </div>
        </template>

        <script>
        export default {
            data: function(){
                return{
                    flag: true,
                }
            },
            methods: {
                changecolor: function () {
                    this.flag = !this.flag;
                }
            },
        }
        </script>

        <style>
        .box {
            display: block;
            width: 100px;
            height: 100px;
            margin: 50px;
        }
        .blue {
            background-color: blue;
        }
        .green {
            background-color: green;
        }
        </style>

在上述的代码中，我们需要学到以下几个问题：

1. 可以使用条件表达式选择有效的类名。
2. 当同时使用多个类名时，要使用方括号。
