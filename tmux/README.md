# Tmux Cheat Sheet

    http://tmuxcheatsheet.com

## 1.:new 创建一个tmux

    tmux #创建一个 windows
    tmux new
    tmux new-session

## 2.激活
    tmux attach -t mysession
    tmux attach -t

## 3.实用操作

### 1) 分屏
    ctrl + b  s 选择windows
    ctrl + b  % 水平分屏
    ctrl + b  " 垂直分屏

### 1) 选择激活的窗口
    ctrl + b up/down/left/right   选择激活窗口

### 3)设置为复制模式 写入配置文件:~/.tmux.conf
    set-window-option -g mode-keys vi
