## 触摸板
由于dwm的原因，触摸板没办法使用所以我们进行一些配置  

>由于本人又回到plasma,plasma触摸板配置不需要另外操心，加上还有许不足，仅供参考


### 安装
```bash
sudo pacman -S libinput
sudo pacman -S xf86-input-synaptics
```
### 配置
```
sudo cp /usr/share/X11/xorg.conf.d/70-synaptics.conf /etc/X11/xorg.conf.d
```

/etc/X11/xorg.conf.d/70-synaptics.conf

```
Section "InputClass"
	Identifier "touchpad"
	Driver "synaptics"
	MatchIsTouchpad "on"
	Option "TapButton1" "1"
	Option "TapButton2" "3"
	Option "TapButton3" "0"
	Option "VertEdgeScroll" "on"
	Option "VertTwoFingerScroll" "on"
	Option "HorizEdgeScroll" "on"
	Option "HorizTwoFingerScroll" "on"
	Option "VertScrollDelta" "-112"
	Option "HorizScrollDelta" "-114"
	Option "MaxTapTime" "125"
EndSection
```

---
[返回到上一页](https://storm-1614.github.io/blog-linux/)  
[返回到主页](https://storm-1614.github.io/)  
