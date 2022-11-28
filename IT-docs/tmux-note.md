Tmux note
=========

| 分类      | 按键         |  含义                        |
| --------- | ------------ | ---------------------------- |
| 引导键    | Ctrl+b       | 激活控制台；此时以下按键生效 |
| 系统操作  | ?            | 列出所有快捷键；按q返回 |
|           | d            | 脱离当前会话；这样可以暂时返回Shell界面，输入tmux attach能够重新进入之前的会话 |
|           | D            | 选择要脱离的会话；在同时开启了多个会话时使用 |
|           | Ctrl+z       | 挂起当前会话 |
|           | r            | 强制重绘未脱离的会话 |
|           | :            | 进入命令行模式；此时可以输入支持的命令，例如kill-server可以关闭服务器 |
|           | [            | 进入复制模式；此时的操作与vi/emacs相同，按q/Esc退出, space 开始复制选区，enter确认复制。<c-b>+] 粘贴, <C-x>+y 复制 |
|           | ~            | 列出提示信息缓存；其中包含了之前tmux返回的各种提示信息 |
| 会话操作  | :new         | 创建会话 |
|           | s            | 选择并切换会话；在同时开启了多个会话时使用 |
|           | $            | 修改会话名称；在同时开启了多个会话时使用 |
| 窗口操作  | c            | 创建新窗口 |
|           | &            | 关闭当前窗口 |
|           | ,            | 重命名当前窗口 `,` |
|           | .            | 修改当前窗口编号；相当于窗口__重新排序__ |
|           | f            | 在所有窗口中查找指定文本 |
|           | p            | 切换至上一窗口 |
|           | n            | 切换至下一窗口 |
|           | l            | 在前后两个窗口间互相切换 |
|           | w            | 通过窗口列表切换窗口 |
|           | 数字键       | 切换至指定窗口 |
| 面板操作  | "            | 将当前面板平分为上下两块 |
|           | %            | 将当前面板平分为左右两块 |
|           | x            | 关闭当前面板 |
|           | !            | 将当前面板置于新窗口；即新建一个窗口，其中仅包含当前面板 |
|           | +            | 将面板拆解到一个新的窗口中编号/或还原 |
|           | -            | 拆解窗口新的面板中 |
|           | Space ⍽      | 在预置的面板布局中循环切换；依次包括even-horizontal、even-vertical、main-horizontal、main-vertical、tiled |
|           | q            | 显示面板编号 |
|           | t            | 显示时钟 |
|           | o            | 在当前窗口中选择下一面板 |
|           | z            | toggle pane zoom |
|           | 方向键       | 移动光标以选择面板 |
|           | Ctrl+方向键  | 以1个单元格为单位移动边缘以调整当前面板大小 |
|           | Alt+方向键   | 以5个单元格为单位移动边缘以调整当前面板大小 |
|           | {            | 向前置换当前面板 |
|           | }            | 向后置换当前面板 |
|           | Alt+o        | 逆时针旋转当前窗口的面板 |
|           | Ctrl+o       | 顺时针旋转当前窗口的面板 |

tmux capture-pane -pS-3|xclip -i -sel clip

set prefix key <c-x>
set -g prefix C-x
unbind C-b
bind C-x send-prefix


tmux shortcuts & cheatsheet

tmux     # start new
tmux new -s myname  # start new with session name
tmux a  #  (or at, or attach)  attach
tmux a -d  #  (or at, or attach)  attach and disconnect all other sessions first
tmux a -t myname          # attach to named
tmux ls          # list sessions
tmux kill-session -t myname        # kill session
tmux ls | grep : | cut -d. -f1 | awk '{print substr($1, 0, length($1)-1)}' | xargs kill        #  Kill all the tmux sessions

In tmux, hit the prefix ctrl+b (my modified prefix is ctrl+a) and then:
List all shortcuts
to see all the shortcuts keys in tmux simply use the bind-key ? in my case that would be CTRL-B ?

Sync Panes
You can do this by switching to the appropriate window, typing your Tmux prefix (commonly Ctrl-B or Ctrl-A) and then a colon to bring up a Tmux command line, and typing:

:setw synchronize-panes
You can optionally add on or off to specify which state you want; otherwise the option is simply toggled. This option is specific to one window, so it won’t change the way your other sessions or windows operate. When you’re done, toggle it off again by repeating the command. tip source

Resizing Panes
You can also resize panes if you don’t like the layout defaults. I personally rarely need to do this, though it’s handy to know how. Here is the basic syntax to resize panes:

PREFIX : resize-pane -D (Resizes the current pane down)
PREFIX : resize-pane -U (Resizes the current pane upward)
PREFIX : resize-pane -L (Resizes the current pane left)
PREFIX : resize-pane -R (Resizes the current pane right)
PREFIX : resize-pane -D 20 (Resizes the current pane down by 20 cells)
PREFIX : resize-pane -U 20 (Resizes the current pane upward by 20 cells)
PREFIX : resize-pane -L 20 (Resizes the current pane left by 20 cells)
PREFIX : resize-pane -R 20 (Resizes the current pane right by 20 cells)
PREFIX : resize-pane -t 2 20 (Resizes the pane with the id of 2 down by 20 cells)
PREFIX : resize-pane -t -L 20 (Resizes the pane with the id of 2 left by 20 cells)
Copy mode:
Pressing PREFIX [ places us in Copy mode. We can then use our movement keys to move our cursor around the screen. By default, the arrow keys work. we set our configuration file to use Vim keys for moving between windows and resizing panes so we wouldn’t have to take our hands off the home row. tmux has a vi mode for working with the buffer as well. To enable it, add this line to .tmux.conf:

setw -g mode-keys vi
With this option set, we can use h, j, k, and l to move around our buffer.

To get out of Copy mode, we just press the ENTER key. Moving around one character at a time isn’t very efficient. Since we enabled vi mode, we can also use some other visible shortcuts to move around the buffer.

For example, we can use "w" to jump to the next word and "b" to jump back one word. And we can use "f", followed by any character, to jump to that character on the same line, and "F" to jump backwards on the line.

   Function                vi             emacs
   Back to indentation     ^              M-m
   Clear selection         Escape         C-g
   Copy selection          Enter          M-w
   Cursor down             j              Down
   Cursor left             h              Left
   Cursor right            l              Right
   Cursor to bottom line   L
   Cursor to middle line   M              M-r
   Cursor to top line      H              M-R
   Cursor up               k              Up
   Delete entire line      d              C-u
   Delete to end of line   D              C-k
   End of line             $              C-e
   Goto line               :              g
   Half page down          C-d            M-Down
   Half page up            C-u            M-Up
   Next page               C-f            Page down
   Next word               w              M-f
   Paste buffer            p              C-y
   Previous page           C-b            Page up
   Previous word           b              M-b
   Quit mode               q              Escape
   Scroll down             C-Down or J    C-Down
   Scroll up               C-Up or K      C-Up
   Search again            n              n
   Search backward         ?              C-r
   Search forward          /              C-s
   Start of line           0              C-a
   Start selection         Space          C-Space
   Transpose chars                        C-t

Configurations Options:
# Mouse support - set to on if you want to use the mouse
* setw -g mode-mouse off
* set -g mouse-select-pane off
* set -g mouse-resize-pane off
* set -g mouse-select-window off

# Set the default terminal mode to 256color mode
set -g default-terminal "screen-256color"

# enable activity alerts
setw -g monitor-activity on
set -g visual-activity on

# Center the window list
set -g status-justify centre

# Maximize and restore a pane
unbind Up bind Up new-window -d -n tmp \; swap-pane -s tmp.1 \; select-window -t tmp
unbind Down
bind Down last-window \; swap-pane -s tmp.1 \; kill-window -t tmp
Resources:
tmux: Productive Mouse-Free Development
How to reorder windows

