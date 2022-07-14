## fcitx5安装配置
### 安装
安装fcitx5：  
``` bash
sudo pacman -S fcitx5-im fcitx5-chinese-addons fcitx5-pinyin-moegirl fcitx5-pinyin-zhwiki
```
配置环境变量  
新建文件 ```~/.pam_environment```添加
```
GTK_IM_MODULE DEFAULT=fcitx
QT_IM_MODULE  DEFAULT=fcitx
XMODIFIERS    DEFAULT=\@im=fcitx
INPUT_METHOD  DEFAULT=fcitx
SDL_IM_MODULE DEFAULT=fcitx
GLFW_IM_MODULE DEFAULT=ibus
```
重启后完成
### 美化
```
yay -S fcitx5-nord
```

到fcitx5设置-附加组件-经典用户界面-主题调整 

---
[返回到上一页](https://storm-1614.github.io/blog-linux/)  
[返回到主页](https://storm-1614.github.io/)  

