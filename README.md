# arch_install
cheat_sheet

直接看别人的流程就可以了
我也不用快照之类的 用ext4也无所谓

安装grab的时候我的微星主板要加`--removable`

display manager 用
```
sudo systemctl enable lightdm.service
```

可以先装xfce 然后在装i3 不用编译可以直接用 包括neovim

i3 里面中文输入发默认自启动
```
exec_always --no-startup-id fcitx5
```
linux实现键盘一些键位的转变

```
┌──(ns㉿darkArch)-[~]
└─$ cat ~/.Xmodmap
!----------------------------------------------------------
! Swap Control and Alt keys, both sides
!----------------------------------------------------------

! First clear all modifiers & control
clear control
clear mod1
clear mod4

! Swap Control_L and Alt_L
keycode  64 = Control_L
keycode  37 = Alt_L Meta_L

! Menu becomes Alt_R Meta_R (AltGr)
keycode 135 = Alt_R Meta_R

! Define Control_R and Alt_R similar to Control_L and Alt_L
keycode 108 = Control_L
keycode 105 = Alt_L Meta_L

! We need to set keycodes first, as some programs (emacs!) read
! the key names and seem to ignore what's below.
add mod1    = Alt_L Alt_R Meta_L Meta_R
add mod4    = Super_L Super_R
add control = Control_L Control_R



remove Lock = Caps_Lock
keysym Escape = Caps_Lock
keysym Caps_Lock = Escape
add Lock = Caps_Lock
```

改变的一些点比如zshshell不如用oh-my-zsh

主机本来也就没建设透明代理 常用翻墙还是想用clashforwindows 命令行下配合proxychains偶尔也够用了
pacman 和 yay 设置成了中科大的源大部分情况速度还行

yay安装的`google-chrome-stable`得搞个带代理的快捷启动
/usr/local/bin/chrome
```
google-chrome-stable --proxy-server=socks5://127.0.0.1:7890
```
discord
```
http_proxy=socks5://127.0.0.1:7890 https_proxy=socks5://127.0.0.1:7890 /usr/bin/discord --proxy-server="socks5://127.0.0.1:7890"
```

接下来就是有关kvm的部分了

## kvm




