.. title: 一个值得参考的Flask-SQLAlchemy查询案例
.. slug: yi-ge-zhi-de-can-kao-de-flask-sqlalchemycha-xun-an-li
.. date: 2017-02-01 13:27:19 UTC+08:00
.. tags: flask, sqlalchemy
.. category: Python
.. link: 
.. description: 
.. type: text

    .. code-block:: bash

        account = db.session.query(
            Account.account_id, Account.account_item,
            Account.account_money, AccountType.type_text,
            Account.account_date, Account.account_addition,
            User.user_email).outerjoin(
            AccountType, Account.account_type == AccountType.type_id).outerjoin(
            User, Account.account_user == User.user_id).order_by(
            Account.account_date.desc()).offset((page-1)*perpage).limit(perpage).all()

在这个例子中，我们查询的是：

按日期降序排列，每页perpage条记录，返回第page页的账目数据，将账目数据中的账目类型编号替换成类型名称，将账目数据中的用户编号替换成用户邮箱。
