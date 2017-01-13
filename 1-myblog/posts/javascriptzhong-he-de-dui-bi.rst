.. title: JavaScript中==和===的对比
.. slug: javascriptzhong-he-de-dui-bi
.. date: 2017-01-13 15:10:28 UTC+08:00
.. tags: javascript
.. category: javascript
.. link: 
.. description: 
.. type: text

JavaScript中的==和===一直是个复杂的问题。对此我们进行了实验，代码如下：

    .. code-block:: html
        :number-lines:

        <template>
        <div id="todoitem">
            <pre>
                var a = {'1': 'a', '2': 'b'};
                var b = {'1': 'a', '2': 'b'};
                var c = a;
            </pre>
            <table>
                <tr class="header">
                    <td>A</td>
                    <td>B</td>
                    <td>A==B</td>
                    <td>A===B</td>
                </tr>
                <tr v-for="item in items">
                    <td>
                        {{item[0]}}
                    </td>
                    <td>
                        {{item[1]}}
                    </td>
                    <td>
                        {{item[2]}}
                    </td>
                    <td>
                        {{item[3]}}
                    </td>
                </tr>
            </table>
        </div>
        </template>
        <script>
            export default {
                data: function () {
                    var a = {'1': 'a', '2': 'b'};
                    var b = {'1': 'a', '2': 'b'};
                    var c = a;
                    return {
                        items: [
                            ["1", "1", 1==1, 1===1],
                            ["1", "'1'", 1=='1', 1==='1'],
                            ["String(1)", "'1'", String(1)=='1', String(1)==='1'],
                            ["parseInt('1')", "1", parseInt('1')==1, parseInt('1')===1],
                            ["1.1", "'1.1'", 1.1=='1.1', 1.1==='1.1'],
                            ["a", "b", a==b, a===b],
                            ["a", "c", a==c, a===c],
                            ["null", "undefined", null==undefined, null===undefined],
                            ["NaN", "0", NaN==0, NaN===0],
                            ["NaN", "null", NaN==null, NaN===null],
                            ["NaN", "undefined", NaN==undefined, NaN===undefined],
                        ]
                    }
                },
            }
        </script>
        <style scoped>
            .header td{
                color: blue;
            }
            table {
                border-collapse: collapse;
            }
            table td{
                border: solid 2px green;
            }
        </style>

输出结果：

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/jsequal.PNG

我只想说，如果===结果符合测试预期，我一定会一直用===，直到哪天发现==有实际价值，再记住使用的环境。