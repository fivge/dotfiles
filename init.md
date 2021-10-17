## term

> oh-my-zsh

<https://ohmyz.sh/>

> git

```bash
git config --global credential.helper store
```

> AUR

`yay`

<https://mirrors.tuna.tsinghua.edu.cn/help/AUR/>

> clock

```bash
hwclock --systohc
```

> user

```bash
useradd -m -G wheel -s /bin/bash x
```

> net

## global

### proxy

> v2ray

<https://wiki.archlinux.org/index.php/V2Ray_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)>

[v2rayA](https://github.com/v2rayA/v2rayA)

> 系统代理

```bash
### 设置系统代理
export http_proxy="http://127.0.0.1:10809"
export https_proxy=$http_proxy

### 取消设置系统代理
unset http_proxy
unset https_proxy

### 设置git代理
git config --global http.proxy $http_proxy
git config --global https.proxy $http_proxy

### 取消设置git代理
git config --global --unset http.proxy
git config --global --unset https.proxy

### 设置ssh代理
ssh -o ProxyCommand="nc -X 5 -x 127.0.0.1:1080 %h %p" root@server
```

> privoxy

`config`

```
listen-address  localhost:8118
forward-socks5   /               127.0.0.1:1080 .
```

```bash
### 启动
systemctl start privoxy
```

> chrome

```bash
### chrome 使用代理启动
sudo google-chrome --proxy-server="socks5://127.0.0.1:1080" --no-sandbox
```

### fonts

https://wiki.archlinux.org/title/Fonts_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)

> 字体目录

- `~/.local/share/fonts` (~/.fonts/ 现在已经过时了)
- `/usr/share/fonts`

> 查看字体

```bash
# 终端
showconsolefont
# X
fc-list :lang="zh_CN"
fc-list :lang="zh"
fc-list | grep Awesome
fc-match FontAwesome
```

> 安装字体

**支持的字体格式** TODO

只需要复制字体文件到字体目录下，然后刷新字体缓存即可

```bash
# 刷新
fc-cache -vf
```

> 推荐字体

- <https://wiki.archlinux.org/index.php/Microsoft_fonts_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)>
- <https://github.com/source-foundry/Hack>
- <https://github.com/microsoft/cascadia-code>
- SF Pro
  <https://developer.apple.com/fonts/>
- Font Awesome
  https://fontawesome.com/
  https://archlinux.org/packages/community/any/ttf-font-awesome/
- noto-emoji
  https://github.com/googlefonts/noto-emoji
- https://fonts.google.com

### input/output

> fcitx

<https://wiki.archlinux.org/index.php/Fcitx_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)>

TODO

> 触摸板手势

<https://zhuanlan.zhihu.com/p/116957768>

<https://github.com/bulletmark/libinput-gestures>

TODO

> Razer 驱动

<https://openrazer.github.io/>

<https://aur.archlinux.org/packages/openrazer-meta/>

```bash
yay -S openrazer-meta
```

TODO

## desktop

> Firefox

- `firefox`
- `firefox-developer-edition`
- `firefox-kde-opensuse`

> Microsoft Edge

<https://www.microsoftedgeinsider.com/zh-cn/>

> VS Code

- <https://code.visualstudio.com/>
- <https://code.visualstudio.com/insiders/>

> Typora

https://theme.typora.io/

> 取色器

```bash
yay -S pick-colour-picker
```

## [beauty](./beauty.md)

## Tools

### dev tools

> docker

> mycli

### other

> aria2

> Watson

https://github.com/TailorDev/Watson

## virtual

> macOS

<https://github.com/sickcodes/Docker-OSX>
