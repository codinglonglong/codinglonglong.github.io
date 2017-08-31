.. title: UEditor的Python迁移
.. slug: ueditorde-pythonqian-yi
.. date: 2015-09-08 09:21:16 UTC+08:00
.. tags: Python, UEditor, Bottle
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

UEditor http://ueditor.baidu.com/website/ 是由百度前端研发部开发的所见即所得开源富文本web编辑器，官方文档 http://fex.baidu.com/ueditor/ 提供了JSP、PHP、ASP.net和ASP的后端部署，没有Python的。而我们的网站建设中，需要用到UEditor，所以研究了一下UEditor的Python迁移，主要是针对Bottle框架的Python迁移。

代码结构如下：
::
        
    >> long@happytime:~/development/frameworktest$ ls
    >> bll  db   documentations  models  readme.md  static  views
    >> dal  dml  main.py         pages   rpl        tools
    >> long@happytime:~/development/frameworktest$ cd static
    >> long@happytime:~/development/frameworktest/static$ ls
    >> css  files  images  js  ueditor
    >> long@happytime:~/development/frameworktest/static$ cd ueditor/
    >> long@happytime:~/development/frameworktest/static/ueditor$ ls
    >> dialogs     lang    third-party         umeditor.min.js
    >> index.html  themes  umeditor.config.js

1、把UEditor的代码放到项目的static/ueditor中，放置结构如上图。

2、main.py完成静态资源文件的映射，代码如下：

.. code-block :: python
    :linenos:

    @route("/static/<path:re:.*>")
    def getstaticdir(path):
        path = "./static/" + str(path)
        return static_file(path, root=".")
        
3、修改umeditor.config.js：

::

    //图片上传配置区
    ,imageUrl: "/imageup"             //图片上传提交地址
    ,imagePath: ""                     //图片修正地址，引用了fixedImagePath,如有特殊需求，可自行配置
    ,imageFieldName:"upfile"                   //图片数据的key,若此处修改，需要在后台对应文件修改对应参数

4、将UEditor放到页面上，views下任意一个tpl文件中：

.. code-block :: html
    :linenos:
    
    <link href="/static/ueditor/themes/default/css/umeditor.css" type="text/css" rel="stylesheet">
    <script type="text/javascript" src="/static/ueditor/third-party/jquery.min.js"></script>
    <script type="text/javascript" charset="utf-8" src="/static/ueditor/umeditor.config.js"></script>
    <script type="text/javascript" charset="utf-8" src="/static/ueditor/umeditor.min.js"></script>
    <script type="text/javascript" src="/static/ueditor/lang/zh-cn/zh-cn.js"></script>

    <div id="editor">
    <script type="text/plain" id="myEditor" style="width:1000px;height:240px;">
    <p>这里我可以写一些输入提示</p>
    </script>
    <script type="text/javascript">
    var um = UM.getEditor('myEditor');
    function getAllHtml() {
        var arr = [];
        arr.push(UM.getEditor('myEditor').getAllHtml());
        window.location.href="/getallhtml?contentstr=" + encodeURIComponent(arr.join("\n"));
    }
    function getContent() {
        var arr = [];
        arr.push(UM.getEditor('myEditor').getContent());
        window.location.href="/getallhtml?contentstr=" + encodeURIComponent(arr.join("\n"));
    }
    function getContentTxt() {
        var arr = [];
        arr.push(UM.getEditor('myEditor').getContentTxt());
        window.location.href="/getallhtml?contentstr=" + encodeURIComponent(arr.join("\n"));
    }
    function hasContent() {
        var arr = [];
        arr.push(UM.getEditor('myEditor').hasContents());
        alert(arr.join("\n"));
    }
    function setFocus() {
        UM.getEditor('myEditor').focus();
    }
    function doBlur(){
        um.blur();
    }
    function setContent() {
        UM.getEditor('myEditor').setContent('欢迎使用umeditor');
    }
    function setDisabled() {
        UM.getEditor('myEditor').setDisabled('fullscreen');
        disableBtn("enable");
    }
    function setEnabled() {
        UM.getEditor('myEditor').setEnabled();
        enableBtn();
    }
    </script>
    </div>
    <div id="btns">
        <table>
            <tr>
                <td>
                    <button class="btn" onclick="getAllHtml()">获得整个html的内容</button>&nbsp;
                    <button class="btn" onclick="getContent()">获得内容</button>&nbsp;
                    <button class="btn" onclick="getContentTxt()">获得纯文本</button>&nbsp;
                    <button class="btn" onclick="hasContent()">判断是否有内容</button>
                </td>
            </tr>
            <tr>
                <td>
                    <button class="btn" onclick="setFocus()">编辑器获得焦点</button>&nbsp;
                    <button class="btn" onclick="doBlur()">编辑器取消焦点</button>&nbsp;
                    <button class="btn" onclick="setContent()">插入给定的内容</button>&nbsp;
                    <button class="btn" onclick="setEnabled()">可以编辑</button>&nbsp;
                    <button class="btn" onclick="setDisabled()">不可编辑</button>
                </td>
            </tr>
            <tr>
                <td>
                    <button class="btn" onclick="UM.getEditor('myEditor').setHide()">隐藏编辑器</button>&nbsp;
                    <button class="btn" onclick="UM.getEditor('myEditor').setShow()">显示编辑器</button>&nbsp;
                    <button class="btn" onclick="UM.getEditor('myEditor').setHeight(300)">设置编辑器的高度为300</button>&nbsp;
                    <button class="btn" onclick="UM.getEditor('myEditor').setWidth(1200)">设置编辑器的宽度为1200</button>
                </td>
            </tr>
        </table>
    </div>

注意，由于要提交的内容本身含有特殊字符，如空格。需要用javascript的encodeURIComponent函数进行编码。

5、编写后台接收提交的代码main.py或者rpl下的任意一个py文件中:

.. code-block :: python
    :linenos:

    @route('/imageup', method="POST")
    def imageup():
        fileobj = request.POST.upfile
        filename = fileobj.filename
        content = fileobj.file.read()
        imagedir = os.getcwd() + "/static/images"
        webimagedir = "/static/images"
        newimagename = str(uuid.uuid1()) + filename
        imageurl = imagedir + "/" + newimagename
        webimageurl = webimagedir + "/" + newimagename
        fout = open(imageurl, "wb")
        fout.write(content)
        fout.close()
        return """{'url':'""" + str(webimageurl) + """',
        'title': '""" + str(newimagename) + """',
        'original':'""" + str(filename) + """',
        'state':'SUCCESS'}"""


    @route('/getallhtml')
    def getallhtml():
        contentstr = request.GET.contentstr
        resultstr = urllib.parse.unquote(contentstr)
        print(resultstr)


    @route('/getcontent')
    def getcontent():
        contentstr = request.GET.contentstr
        resultstr = urllib.parse.unquote(contentstr)
        print(resultstr)


    @route('/getcontenttxt')
    def getcontenttxt():
        contentstr = request.GET.contentstr
        resultstr = urllib.parse.unquote(contentstr)
        print(resultstr)

可以看到，由于之前的javascript中进行了编码，所以这里要用urllib.parse.unquote进行解码。而上传的图片，会放到/static/images目录下。

至此就完成了UEditor的Python迁移，可以正常在Bottle框架上完成工作。

注：例子中使用的是UEditor的缩减版UMeditor。
