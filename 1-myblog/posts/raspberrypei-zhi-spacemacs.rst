.. title: Raspberry配置Spacemacs
.. slug: raspberrypei-zhi-spacemacs
.. date: 2017-03-18 14:30:12 UTC+08:00
.. tags: Raspberry, Spacemacs
.. category: Emacs
.. link: 
.. description: 
.. type: text


1、安装Emacs。

    ::

        >> wget http://mirrors.ustc.edu.cn/gnu/emacs/emacs-25.1.tar.gz
        >> tar zxvf emacs-25.1.tar.gz
        >> cd emacs-25.1
        >> sudo apt install libxpm-dev libgif-dev
        >> sudo apt install libtinfo-dev
        >> ./configure
        >> sudo make
        >> sudo make install

2、安装Spacemacs。

    ::

        >> git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d
        >> vi .emacs.d/core/core-configuration-layer.el
            (defvar configuration-layer--elpa-archives
            '(("melpa" . "https://mirrors.tuna.tsinghua.edu.cn/elpa/melpa/")
                ("org"   . "https://mirrors.tuna.tsinghua.edu.cn/elpa/org/")
                ("gnu"   . "https://mirrors.tuna.tsinghua.edu.cn/elpa/gnu/")
                ("marmalade" . "https://mirrors.tuna.tsinghua.edu.cn/elpa/marmalade/"))
            "List of ELPA archives required by Spacemacs.")
        >> emacs
        
3、配置Spacemacs。

    ::

        >> sudo apt install python-jedi python3-jedi python-virtualenv python-autopep8
        >> emacs
        >> M-x configuration-layer/create-layer
            myconf
        >> C-x C-c
        >> emacs ~/.emacs.d/private/myconf/config.el
            ;; 切换输入法
            (global-unset-key (kbd "C-SPC"))
            (global-set-key (kbd "M-SPC") 'set-mark-command)

            ;; 中文字体
            (set-fontset-font "fontset-default" 'unicode '("WenQuanYi Zen Hei"))

            ;; Code Review
            (defun add-code-review-note ()
            "Add note for current file and line number"
            (interactive)
            (let ((file-name (buffer-file-name))
                    (file-line (line-number-at-pos)))
                (switch-to-buffer-other-window (get-buffer-create "NOTES"))
                (goto-char (point-min))
                (when (not (search-forward "-*- mode:compilation-shell-minor"
                                            nil t))
                (compilation-shell-minor-mode 1)
                (insert "-*- mode:compilation-shell-minor -*-\n\n"))
                (goto-char (point-max))
                (if (/= (current-column) 0)
                    (newline))
                (insert file-name ":" (number-to-string file-line) ": ")))

            (global-set-key (kbd "C-c r") 'add-code-review-note)

            ;; Copy region or whole line
            (global-set-key "\M-w"
            (lambda ()
            (interactive)
            (if mark-active
                (kill-ring-save (region-beginning)
                (region-end))
                (progn
                (kill-ring-save (line-beginning-position)
                (line-end-position))
                (message "copied line")))))


            ;; Kill region or whole line
            (global-set-key "\C-w"
            (lambda ()
            (interactive)
            (if mark-active
                (kill-region (region-beginning)
            (region-end))
                (progn
                (kill-region (line-beginning-position)
            (line-end-position))
                (message "killed line")))))

            ;; 切换最大化
            (global-set-key [f12] 'my-maximized)
            (defun my-maximized ()
            (interactive)
            (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
                                    '(2 "_NET_WM_STATE_MAXIMIZED_HORZ" 0))
            (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
                                    '(2 "_NET_WM_STATE_MAXIMIZED_VERT" 0)))

            ;; 切换半透明
            (global-set-key [f8] 'loop-alpha)
            (setq alpha-list '((100 100) (85 85) (35 35)))
            (defun loop-alpha ()
            (interactive)
            (let ((h (car alpha-list)))
                ((lambda (a ab)
                (set-frame-parameter (selected-frame) 'alpha (list a ab))
                (add-to-list 'default-frame-alist (cons 'alpha (list a ab)))
                ) (car h) (car (cdr h)))
                (setq alpha-list (cdr (append alpha-list (list h))))
                )
            )
            (loop-alpha)

            ;; 优化注释
            (defun qiang-comment-dwim-line (&optional arg)
            (interactive "*P")
            (comment-normalize-vars)
            (if (and (not (region-active-p)) (not (looking-at "[ \t]*$")))
                (comment-or-uncomment-region (line-beginning-position)
                (line-end-position))
                (comment-dwim arg)))
            (global-set-key "\M-;" 'qiang-comment-dwim-line)

            ;; Y or N
            (fset 'yes-or-no-p 'y-or-n-p)

            ;; Neotree
            (global-set-key [f9] 'neotree-toggle)

            ;; Line number
            (global-linum-mode 1)

            ;; Python mode
            (add-to-list 'auto-mode-alist '("\\.py?\\'" . python-mode))

            ;; autopep8
            (add-hook 'python-mode-hook 'py-autopep8-enable-on-save)

            ;; Fold
            (add-hook 'python-mode-hook 'hideshowvis-enable)

            ;; Mic-paren
            (add-hook 'python-mode-hook 'paren-activate)

            ;; Jedi
            (autoload 'jedi:setup "jedi" nil t)
            (add-hook 'python-mode-hook 'jedi:setup)
            (setq jedi:setup-keys t)                 
            (setq jedi:complete-on-dot t)  

            ;; Python mode
            (setq py-python-command "ipython3")
            (global-set-key [f5]  'run-python)
            (add-hook 'python-mode-hook 'yas-global-mode)

            ;; Web mode
            (add-to-list 'auto-mode-alist '("\\.tpl\\'" . html-mode))
            (add-to-list 'auto-mode-alist '("\\.html\\'" . html-mode))
            (add-to-list 'auto-mode-alist '("\\.xml\\'" . html-mode))
            (add-to-list 'auto-mode-alist '("\\.css\\'" . css-mode))
            (add-to-list 'auto-mode-alist '("\\.js\\'" . js-mode))
            (add-hook 'html-mode-hook 'web-mode)
            (add-hook 'css-mode-hook 'web-mode)
            (add-hook 'js-mode-hook 'web-mode)
            (add-hook 'web-mode-hook 'global-auto-complete-mode)
            (add-hook 'web-mode-hook 'rainbow-mode)
            (add-hook 'web-mode-hook 'emmet-mode)
            (add-hook 'web-mode-hook 'hideshowvis-enable)


            ;; Auto complete
            (add-hook 'c-mode-hook 'auto-complete-mode)
            (add-hook 'c-mode-hook 'yas-global-mode)
            (setq ac-quick-help-prefer-pos-tip t)
            (setq ac-use-quick-help t)
            (setq ac-quick-help-delay 1.0)
            (setq ac-fuzzy-enable t)
            (setq ac-auto-start 1)
            (setq ac-quick-help-delay 0.5)

            ;; Yas
            (global-set-key (kbd "C-c C-x 3") 'yas/expand)
            (global-set-key (kbd "C-c C-x 4") 'yas/next-field)
        >> C-x C-s
        >> C-x C-c
        >> emacs ~/.spacemacs
            dotspacemacs-configuration-layers
            '(
                python
                ;; ----------------------------------------------------------------
                ;; Example of useful layers you may want to use right away.
                ;; Uncomment some layer names and press <SPC f e R> (Vim style) or
                ;; <M-m f e R> (Emacs style) to install them.
                ;; ----------------------------------------------------------------
                helm
                auto-completion
                better-defaults
                emacs-lisp
                ;; git
                markdown
                org
                myconf
                ;; (shell :variables
                ;;        shell-default-height 30
                ;;        shell-default-position 'bottom)
                ;; spell-checking
                ;; syntax-checking
                ;; version-control
                )

            dotspacemacs-additional-packages '(
                                        minimap
                                        py-autopep8
                                        jedi
                                        mic-paren
                                        hideshowvis
                                        emmet-mode
                                        python
                                        python-mode
                                        web-mode
                                        auto-complete
                                        pos-tip
                                        fuzzy
                                        popup
                                        rainbow-mode
                                        yasnippet)
        >> C-x C-s
        >> C-x C-c
        >> emacs
        >> M-x jedi:install-server

