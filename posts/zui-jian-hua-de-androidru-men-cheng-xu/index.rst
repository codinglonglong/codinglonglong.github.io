.. title: 最简化的Android入门程序
.. slug: zui-jian-hua-de-androidru-men-cheng-xu
.. date: 2017-07-14 19:57:48 UTC+08:00
.. tags: Android, java
.. category: Android
.. link: 
.. description: 
.. type: text


用Android Studio创建的空项目包含好几个文件夹和文件，最核心的文件其实只有三个： 

1. manifests目录下的AndroidManifest.xml

2. java目录下的MainActivity.java

3. layout目录下的activity_main.xml

以下是一个最简单的Android程序，启动后是一个空的页面。


1. AndroidManifest.xml

.. code-block:: xml
    :number-lines:

    <?xml version="1.0" encoding="utf-8"?>
    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
        package="com.example.along.homebank">

        <application
            android:icon="@mipmap/ic_launcher"
            android:label="@string/app_name"
            android:theme="@style/AppTheme">
            <activity
                android:name=".MainActivity"
                android:label="@string/title_activity_main">
                <intent-filter>
                    <action android:name="android.intent.action.MAIN"/>
                    <category android:name="android.intent.category.LAUNCHER"/>
                </intent-filter>
            </activity>
        </application>

    </manifest>


最关键的是 **<intent-filter>** 部分，里面设置了MainActivity是默认启动的Activity。


2. MainActivity.java

.. code-block:: java
    :number-lines:

    package com.example.along.homebank;

    import android.os.Bundle;
    import android.support.v7.app.AppCompatActivity;

    public class MainActivity extends AppCompatActivity {

        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);
        }
    }



最关键的是 **setContentView(R.layout.activity_main);** ，里面设置了程序创建时要渲染的layout，也就是界面。


3. activity_main.xml

.. code-block:: xml
    :number-lines:

    <?xml version="1.0" encoding="utf-8"?>
    <android.support.design.widget.CoordinatorLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:context="com.example.along.homebank.MainActivity">
    </android.support.design.widget.CoordinatorLayout>

这个布局文件基本是空的，因为我们什么都没有放进去，所以程序运行时是一个白屏。

从这个最基本的Android程序中，我们可以看到一种程序设计的通用模式："配置+逻辑+布局"。
配置负责控制一些全局的东西，逻辑负责控制整个程序的逻辑实现，布局负责控制用户交互。
就好比做网站，一些JavaScript文件负责配置，大部分JavaScript负责逻辑，HTML和CSS负责布局。
再经过合理的连接，形成配合，共同完成任务。不得不说，有一种程序设计上的"秩序美"。
而这种有秩序的紧密配合，在程序开发中处处可见。
也许这种美就是"自顶向下，逐步求精"和"模块化"两大思想的最好体现。
