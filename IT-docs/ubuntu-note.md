Ubuntu Notes
============

```
WINDOWID=`xwininfo -name 'dclock'|grep xwininfo|awk '{print $4}'`
xprop -id $WINDOWID -format _NET_WM_STATE 32a -set _NET_WM_STATE _NET_WM_STATE_ABOVE
xprop -id $WINDOWID -format _MOTIF_WM_HINTS 32c -set _MOTIF_WM_HINTS 2
xdotool windowsize --sync $WINDOWID 96 44
xdotool windowmove --sync $WINDOWID 1297 2485
wmctrl -i -r $WINDOWID -b toggle,above
```



xdotool key [key name]
xdotool key alt+Tab
xdotool type 'word'
xdotool search --name [window name] key [key name] 查找窗口并按键
xdotool mousemove x y
xdotool mousemove x y click 1  1左键 2滚轮 3右键 4向上滚 5向下滚
xdotool search --title "..."
xdotool key Return 模拟回车键
xdotool keydown/keyup super 按下Win键不放
xdotool key Super_L 左Win
watch -n 10 xdotool key Return 搭配watch使用，实现循环10秒敲击一次回车
xdotool search "Firefox"  获取窗口名称
xdotool getwindowname 39845889 在以上指令列出的ID中获取容器名称
xdotool getactivewindow 获取当前激活的窗口
xdotool windowminimize 最小化窗口
xdotool windowminimize $(xdotool getactivewindow) 最小化当前窗口
xdotool key ctrl+l BackSpace 点击ctrl+l，然后是BackSpace键
xdotool search --name gdb key ctrl+c 在窗口名为gdb上点击ctrl+c
xdotool mousemove_relative 10 10 鼠标相对移动
xdotool mousemove_relative --sync 10 10 异步鼠标相对移动
xdotool click -repeat 1 3  鼠标右键点击1次
xdotool mousedown/mouseup
xdotool getmouselocation 获取鼠标位置
xdotool getmouselocation --shell 获取鼠标位置(便于获取数据)

eval $(xdotool getmouselocation --shell)
echo $X,$Y
即可获得X，Y位置

xdotool getactivewindow windowmove 10 10 移动当前窗口位置

xdotool search "XXXX"
如果存在，会列出该进程下所有窗体的编号（当然编号看起来不方便，但好歹有）

彷佛以下这条命令更加实用点
xdotool search "XXXX" getwindowname %@

这样可以显示所有窗体的title（如果不加%@ 则显示第一条，反而不是很好用）


还可以以下一些命令：
xdotool search . getwindowpid %@

//查找所有窗体，所在的 进程号（进程号一样，说明是同一个进程）

xdotool search . getwindowname %@
//查找所有窗体，并显示窗体的title


wmctrl -i -r $WINDOWID -b toggle,above #move window topmost

