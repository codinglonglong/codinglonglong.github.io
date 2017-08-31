.. title: 清空音乐文件的标签以避免播放器显示乱码
.. slug: qing-kong-yin-le-wen-jian-de-biao-qian-yi-bi-mian-bo-fang-qi-xian-shi-luan-ma
.. date: 2017-09-01 03:41:02 UTC+08:00
.. tags: 音乐标签, 乱码
.. category: Python
.. link: 
.. description: 
.. type: text


有时候我们拿到的音乐文件会包含专辑、歌手、音轨、年份等等标签信息，英文的还好，但是中文的，跨操作系统的时候就容易出现乱码。这时放到播放器里，十分影响观感，那不如把这些信息都清空。


.. code-block :: python
    :linenos:

    import os
    from mutagenx.easyid3 import EasyID3
    from mutagenx.easymp4 import EasyMP4
    baseurl = "C:/musics"
    flist = os.listdir(baseurl)
    for f in flist:
        fname = baseurl + "/" + f
        if fname.endswith(".mp3"):
            try:
                m = EasyID3(fname)
            except Exception as e:
                print(e)
        elif fname.endswith(".mp4") or fname.endswith(".m4a"):
            try:
                m = EasyMP4(fname)
            except Exception as e:
                print(e)
        else:
            print(fname) + " is unable to be converted."
        m["title"] = ""
        m["album"] = ""
        m["artist"] = ""
        m["tracknumber"] = "0"
        m["genre"] = ""
        m["date"] = ""
        m.save()
