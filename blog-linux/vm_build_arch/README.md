## 在虚拟机安装archlinux
### 环境
环境：VirtualBox  
镜像：archlinux livecd 2022.6
### 创建虚拟机
只需要创建一个类型为archlinux的虚拟机就好
### 换源
在成功进入到命令行后首先需要换源  
``` bash
reflector -c China --save /etc/pacman.d/mirrorlist
systemctl stop reflector
pacman -Sy
```
### 分区&挂载
使用cfdisk分区，只需要将所有空间分给linux filesystem就好了  
用`mkfs.ext4`进行格式化  
``` bash
mkfs.ext4 /dev/sda1
```
然后挂载
``` bash
mount /dev/sda1 /mount
```
### 安装基本系统
用`pacstrap`脚本安装基本系统
``` bash
pacstrap /mnt linux linux-firmware base base-devel neovim networkmanager grub
```
### 进入基本系统
写入分区表  
``` bash
genfstab -U /mnt >> /mnt/etc/fstab
```
然后进入基本系统：
``` bash
arch-chroot /mnt
```
### 安装引导
``` bash
grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
passwd root
systemctl enable NetworkManager
```

