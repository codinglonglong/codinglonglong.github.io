.. title: Docker中Emacs支持退格
.. slug: dockerzhong-emacszhi-chi-tui-ge
.. date: 2017-01-30 22:03:15 UTC+08:00
.. tags: Docker, Emacs
.. category: Emacs
.. link: 
.. description: 
.. type: text

默认在Docker中，Emacs使用退格无法删除光标前的字符，而是显示帮助信息，这让人有些费解，可以采用如下方法解决：

    .. code-block:: bash

        emacs ~/.emacs
        (global-set-key "\C-h" 'backward-delete-char-untabify)
        (global-set-key "\d" 'delete-char)
        C-x C-s
        C-x C-c

这时再用emacs命令打开文件，就可以正常使用退格键删除光标前的字符了。

