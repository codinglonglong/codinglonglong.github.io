.. title: vuejs学习(8)
.. slug: vuejsxue-xi-8
.. date: 2017-01-14 15:07:00 UTC+08:00
.. tags: vuejs, javascript, vue-cli
.. category: javascript
.. link: 
.. description: 
.. type: text

本文要学习的是列表渲染 v-for ，看测试代码 **TodoItem.vue** ：

    .. code-block:: html
        :number-lines:

        <template>
        <div id="todoitem">
            <ul>
                <li v-for="item in items1">{{item}}</li>
            </ul>
            <table border="1">
                <tr>
                    <td>项1</td>
                    <td>项2</td>
                    <td>索引</td>
                </tr>
                <tr v-for="item, index in items2">
                    <td>{{item[0]}}</td>
                    <td>{{item[1]}}</td>
                    <td>{{index}}</td>
                </tr>
            </table>
            <ul>
                <li v-for="value, key, index in items3">{{index}}==>{{key}}==>{{value}}</li>
            </ul>
            <ul>
                <li v-for="item in 3">{{item}}</li>
            </ul>
            <ul>
                <template v-for="item in items5" v-if="male">
                    <li>{{item}}</li>
                </template>
                <template v-for="item in items6" v-if="!male">
                    <li>{{item}}</li>
                </template>
            </ul>
        </div>
        </template>

        <script>
        export default {
            data: function () {
                return {
                    items1: [5, 6, 7],
                    items2: [[1, 2], [3, 4], [5, 6]],
                    items3: {
                        'name': 'Tom',
                        'age': 20,
                        'gender': 'male'
                    },
                    male: true,
                    items5: ["Boy1", "Boy2", "Boy3"],
                    items6: ["Girl1", "Girl2", "Girl3"],
                }
            },
        }
        </script>

        <style scoped>
        </style>

运行结果：

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/vueforrender.PNG

在上述的代码中，我们需要学到以下几个问题：

1. vuejs的v-for和Python的for循环有很多相似的地方，比如元素迭代，比如整数迭代。
2. vuejs的迭代可以包含索引，如果是列表，用“item, index in items”；如果是对象，用“value, key, index in items”。
3. v-for迭代的目标也可以是函数的可迭代返回值，比如返回列表。

后面的文章我们将学习更复杂的列表渲染。

