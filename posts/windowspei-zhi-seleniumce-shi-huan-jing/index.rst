.. title: Windows配置Selenium测试环境
.. slug: windowspei-zhi-seleniumce-shi-huan-jing
.. date: 2017-04-06 13:22:14 UTC+08:00
.. tags: Selenium, Python
.. category: Python
.. link: 
.. description: 
.. type: text

1、安装Selenium，参考： https://codinglonglong.github.io/posts/pipshi-yong-guo-nei-yuan/

2、下载浏览器驱动。

    1) IE浏览器： http://selenium-release.storage.googleapis.com/index.html?path=IE.Driver.Beta/

    2) Firefox浏览器： https://github.com/mozilla/geckodriver/releases

    3) Chrome浏览器： https://sites.google.com/a/chromium.org/chromedriver/downloads

    4) Edge浏览器： https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/

3、把上一步中的驱动放到系统可执行目录，或者将该驱动的目录加入系统环境变量。

4、编写代码：

    .. code-block:: python
        :number-lines:

        from selenium import webdriver

        browser1 = webdriver.Firefox()
        browser1.get("https://codinglonglong.github.io/")


        browser2 = webdriver.Chrome()
        browser2.get("https://codinglonglong.github.io/")


        browser3 = webdriver.Edge()
        browser3.get("https://codinglonglong.github.io/")


        browser4 = webdriver.Ie()
        browser4.get("https://codinglonglong.github.io/")

5、运行代码即可自动打开浏览器。

