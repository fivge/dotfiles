# beauty

## 0x01 Display manager

https://wiki.archlinux.org/title/Display_manager_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)

https://wiki.archlinux.org/title/Xprofile_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)

> 加载显示管理器

```bash
file /etc/systemd/system/display-manager.service
```

```
/etc/systemd/system/display-manager.service: symbolic link to /usr/lib/systemd/system/lightdm.service
```

> 会话配置 vm/desktop

- 读取 /usr/share/xsessions/
- 运行 ~/.xinitrc 会话
- 没有窗口管理启动应用程序

> 自启动程序

https://aur.archlinux.org/packages/xinit-xsession/

### sddm

https://wiki.archlinux.org/title/SDDM_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)

```bash
### 安装
sudo pacman -S sddm
### 启用
sudo systemctl enable sddm.service
```

#### theme

https://store.kde.org/p/1312658

https://framagit.org/MarianArlt/sddm-sugar-candy

```bash
git clone https://framagit.org/MarianArlt/sddm-sugar-candy

sddm-greeter --test-mode --theme /usr/share/sddm/themes/sugar-candy
```

### LightDM

[LightDM](https://wiki.archlinux.org/title/LightDM)

## 0x02 Window manager

https://wiki.archlinux.org/title/Window_manager_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)

### 一、i3

#### 1. 安装

> i3? i3-wm? i3-gaps?

**i3-wm 与 i3-gaps (一个 i3 的分支，带有窗口间隙和其它特性)冲突，并且默认状态下将安装 i3-gaps**

```bash
### dnf
sudo dnf install i3-gaps
### pacman
sudo pacman -S i3-gaps
```

#### 2. 启动

##### a. 从 tty 启动

使用 xinit 通过 `startx`命令

##### b. 从显示管理器启动

安装时在 `/usr/share/xsessions`下生成了两个启动文件: `i3.desktop`, `i3-with-shmlog.desktop`

#### 3. 调试

```bash
i3 reload
```

#### 4. 主题

- https://github.com/okraits/j4-make-config
- 参考 <https://github.com/aeghn/prettyi3>

#### 5. 程序启动器

键绑定默认为 `$Mod+d`

#### 6. 面板

- i3bar
- xfce4-panel
- [polybar](https://github.com/jaagr/polybar)
- [excalibar](https://github.com/cylgom/excalibar)

#### 7. 状态

- [conky](https://github.com/brndnmtthws/conky)
- [i3status](https://github.com/i3/i3status)
- [i3blocks](https://github.com/vivien/i3blocks)×
- [i3pystatus](https://github.com/enkore/i3pystatus)×
- [bumblebee-status](https://github.com/tobi-wan-kenobi/bumblebee-status/)值得尝试
- [py3status](https://github.com/ultrabug/py3status)？
- [i3status-rust](https://github.com/greshake/i3status-rust)√

#### 8. 锁屏

- ~~i3lock~~
- [i3lock-color](https://github.com/Raymo111/i3lock-color)

```bash
### 安装
yay -S i3lock-color-git
### 锁屏
i3lock
```

#### 9. 壁纸

- [nitrogen](<https://wiki.archlinux.org/index.php/Nitrogen_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)>)

#### 10. 外接显示器

- [xrandr](<https://wiki.archlinux.org/index.php/Xrandr_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)>)

```bash
xrandr --output HDMI-1-3 --mode 2560x1080 --rate 60 --output eDP1 --auto

xrandr --output HDMI-1-3 --mode 2560x1080 --rate 60 /
```

### 扩展一：程序启动器

通过[Desktop entries](<https://wiki.archlinux.org/title/Desktop_entries_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)>)创建一个已安装应用的列表

- [dmenu](<https://wiki.archlinux.org/title/Dmenu_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)>)
- [dmenu2](https://github.com/spcmd/dmenu2)
- [j4-dmenu-desktop](https://github.com/enkore/j4-dmenu-desktop)
- [rofi](https://github.com/davatorium/rofi)
- [KRunner](<https://wiki.archlinux.org/title/KRunner_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)>)

#### rofi

https://github.com/davatorium/rofi

https://wiki.archlinux.org/title/Rofi

https://www.jianshu.com/p/f25465ca5e73

> themes

https://github.com/adi1090x/rofi.git

https://draculatheme.com/rofi

#### KRunner

`~/.config/i3/config`

```
set $menu --no-startup-id qdbus org.kde.krunner /App display
bindsym $mod+d exec $menu
```

### 扩展二：面板

#### i3bar

#### [polybar](https://github.com/jaagr/polybar)

##### 1. 调试

```bash
install -Dm644 /usr/share/doc/polybar/config $HOME/.config/polybar/config
polybar example
```

##### 2. themes

- https://github.com/adi1090x/polybar-themes
- https://guyueshui.github.io/post/polybar-%E7%9A%84%E9%85%8D%E7%BD%AE%E7%AC%94%E8%AE%B0/

### 扩展三：状态

#### 1. conky

> 不冲突 可以单独使用

https://github.com/brndnmtthws/conky

#### 2. i3status-rust

<https://github.com/greshake/i3status-rust>

https://github.com/greshake/i3status-rust/blob/master/blocks.md

##### a. debug

```bash
i3bar -b "bar-0" reload
```

### 二、i3-gnome

https://github.com/i3-gnome/i3-gnome/

## 0x03 Desktop environment

https://wiki.archlinux.org/title/Desktop_environment_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)

## 0x04 通用

### 一、鼠标

https://sweezy-cursors.com/?s=rick

https://github.com/ful1e5/apple_cursor

https://github.com/varlesh/volantes-cursors

https://wiki.archlinux.org/title/Cursor_themes_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)

### 二、图标

https://wiki.archlinux.org/title/Icons

https://github.com/PapirusDevelopmentTeam/papirus-icon-theme

```bash
sudo pacman -S papirus-icon-theme
```

https://github.com/rtlewis88/rtl88-Themes/tree/Arc-ICONS

### 三、主题颜色

https://material.io/resources/color

https://material.io/design/color/the-color-system.html#tools-for-picking-colors

### 四、字体

见[init](./init.md)
