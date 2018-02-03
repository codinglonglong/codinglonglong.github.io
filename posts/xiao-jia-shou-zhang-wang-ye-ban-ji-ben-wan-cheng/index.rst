.. title: 小家手帐网页版基本完成
.. slug: xiao-jia-shou-zhang-wang-ye-ban-ji-ben-wan-cheng
.. date: 2017-02-25 15:34:06 UTC+08:00
.. tags: 个人作品, Python, vuejs, Docker, javascript, flask, flask-restplus
.. category: 个人作品
.. link: 
.. description: 
.. type: text

利用不到一个月的周末业余时间，使用刚刚接触不久的vuejs，基本完成了小家手帐的网页版。

代码发布到了 https://github.com/codinglonglong/homebankservice 和 https://github.com/codinglonglong/homebankweb 这两个代码仓库。

服务端主要涉及的相关技术点包括：


1. flask_restplus实现的RESTful服务； 
2. sqlalchemy实现的数据库ORM； 
3. TimedRotatingFileHandler实现的滚动日志； 
4. 自定义装饰器实现的权限验证；
5. “接口-接口模型-数据库访问-数据库模型”结构网站的探索；
6. Swagger-UI接口测试的使用。


网页端主要涉及的相关技术点包括：


1. 基于vue-router的页面导航；
2. 基于axios和vue-axios的前后端通信；
3. 基于element-ui的页面交互；
4. 基于vue-cookie的cookie操作；
5. vuejs中多组件的通信。
