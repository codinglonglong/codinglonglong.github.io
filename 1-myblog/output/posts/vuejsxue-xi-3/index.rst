.. title: vuejs学习(3)
.. slug: vuejsxue-xi-3
.. date: 2017-01-11 19:09:36 UTC+08:00
.. tags: vuejs, javascript, vue-cli
.. category: javascript
.. link: 
.. description: 
.. type: text

本文初步学习一下vuejs提供的组件。我们做了一个列表的例子。

**main.js**

    .. code-block:: js
        :number-lines:

        import Vue from 'vue'
        import TodoList from './TodoList'

        new Vue({
            el: '#app',
            template: '<TodoList/>',
            components: { TodoList }
        });

**TodoList.vue**

    .. code-block:: html
        :number-lines:

        <template>
        <div id="todolist">
            <ul>
                <li>父容器1</li>
                <li>父容器2</li>
            </ul>
            <ul>
                <TodoItem todomessage="子容器1"></TodoItem>
                <TodoItem todomessage="子容器2"></TodoItem>
            </ul>
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
        li{
            color: blue;
        }
        </style>


**components/TodoItem.vue**

    .. code-block:: html
        :number-lines:

        <template>
            <li>{{todomessage}}</li>
        </template>

        <script>
        export default {
            props: ['todomessage'],
        }
        </script>

        <style scoped>
        li{
            color: red;
        }
        </style>

在上述的代码中，我们需要学到以下几个问题：

1. 父组件在components里引入了子组件。
2. 父组件通过设定子组件中props涉及到的变量，为子组件传值。
3. 子组件中的css部分要加上scoped，表明该段样式只在这个组件中有效，否则设定样式可能会无效，或者影响其他组件的样式。

下图是加上scoped

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/vue-component-1.PNG

下图是不加scoped

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/vue-component-2.PNG

