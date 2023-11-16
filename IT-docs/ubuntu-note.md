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
```
# Detect the metrics of devices
sensors  # show CPU temperature related info
iwconfig # show wireless network device info

# 手动启动网络连接
dmesg|grep eth0
sudo dhclient en3p40  #eth0 name

```
ls -al /etc/netplan              # get .yaml filename
sudo lshw -C network             # identify ethernet device name, enxxxxxx

#Edit it with:

sudo pico /etc/netplan/*.yaml    # <-- change the * to your filename

#Initially make its content the following, with EXACLY the same spacing, indentation, and no tabs:
#
#    network:
#      version: 2
#      renderer: networkd
#      ethernets:
#        en01:
#          dhcp4: true
#          dhcp6: true
#          optional: true
#      wifis:
#        wlp6s0:
#          dhcp4: true
#          dhcp6: true
#          access-points:
#            "YourWifiNetworkName":
#              password: "WifiNetworkPassword"

sudo netplan generate
sudo netplan apply
reboot
```

sudo vim /etc/resolv.conf

sudo apt install xorg ubuntu-desktop

ESC 进入recovery mode
Ctrl+Alt+F1   GUI
Ctrl+Alt+F2~6 tty1~6
Ctrl+Alt+f7   GUI in some lsb


/etc/xdg/autostart/           # autostart
/usr/share/applications/      # icon show application

# apt fix
sudo apt-get autoremove
sudo apt-get --purge remove && sudo apt-get autoclean
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade && sudo apt-get dist-upgrade
sudo dpkg-reconfigure -a
sudo dpkg --configure -a

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update

* Issue A
> Skipping acquire of configured file 'main/binary-i386/Packages' as repository
> 'https://qgis.org/ubuntu jammy InRelease' doesn't support architecture 'i386'
>
> Solution: add '[arch=amd64]' option

* Issue B
> W: https://qgis.org/ubuntu/dists/jammy/InRelease: Key is stored in legacy
>  trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in
>  apt-key(8) for details.
>
> Solution: sudo apt-key list |grep -iC 5 qgis
>           sudo apt-key --keyring /etc/apt/trusted.gpg export A419C5BE | \
>                    sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/qgis.gpg
>           sudo apt-key --keyring /etc/apt/trusted.gpg del A419C5BE



# .desktop file
/usr/share/applications/
/var/lib/snapd/desktop/applications/


# Unable to enter graphical interface
sudo apt update
sudo apt install ubuntu-desktop unity lightdm
sudo service gdm3 start
sudo systemctl set-default graphical.target
# sudo systemctl set-default multi-user.target

sudo dpkg-reconfigure lightdm


# update DNS conf
```
cat >> /etc/NetworkManager/conf.d/90-dns-none.conf << EOF
[main]
dns=none
EOF

sudo vim /etc/resolv.conf
sudo systemctl restart systemd-resolved
sudo systemctl restart NetworkManager

 /etc/systemd/resolved.conf

```



# Upgrade ubuntu
```
sudo apt-mark showhold
  # If there are on hold, packages, you should unhold the packages with:
	sudo apt-mark unhold <package_name>

 # Refresh the apt list and upgrade all installed packages:
sudo apt update
sudo apt upgrade

 # If the kernel is upgraded, reboot the machine, and once booted log back in:
sudo systemctl reboot

 # Perform a major version upgrade of the installed packages:
sudo apt full-upgrade # apt full-upgrade may also remove some unnecessary packages.

 # Remove all automatically installed dependencies that are no longer needed by any package:
sudo apt --purge autoremove

sudo apt install update-manager-core
sudo do-release-upgrade -d
```

```
sudo lsof -n -w  /dev/nvidia* # show mod using pid
```

apt install nvidia-470-470

apt remove --purge nvidia-470
apt autoremove

sudo apt install linux-{headers,image,modules,modules-extra}-5.8.0-63-generic
sudo apt install linux-{headers,image,modules,modules-extra}-`uname -r`


/usr/share/doc/linux-headers-*
/usr/src/linux-headers-*

sudo apt install linux-headers-`uname -r`  # Install linux headers
cd /usr/src/linux-headers-`uname -r` # Go to linux headers directory
sudo make include/generated/uapi/linux/version.h # Generate version.h
sudo ln -s $PWD/include/generated/uapi/linux/version.h include/version.h # Create symbol link to generate file

/lib/modules/6.1.5-060105-generic$ sudo ln -s /usr/src/linux-headers-6.1.5-060105 build

sudo ./NVIDIA-Linux-x86_64-470.94.run --kernel-source-path /usr/src/linux-headers-5.4.0-1091-gke
--kernel-source-dir


sudo apt install linux-modules-extra-`uname -r`

sudo modprobe snd-hda-intel uvcvideo
sudo apt-get install --reinstall alsa-base pulseaudio
sudo alsa force-reload

