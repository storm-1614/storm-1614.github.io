## ArchLinux UEFI 双系统安装

### 准备  
使用iwctl连网_略  
换源
``` bash
reflector -c China --save /etc/pacman.d/mirrorlist
systemctl stop reflector
```
调整时间
``` bash
timedatectl set-ntp true
```
### 分区
`lsblk`看分区名  
`cfdisk`分区  
格式化分区用`mkfs.ext4`  
挂载swap分区用`mkswap`  
用mount挂载根分区到/mnt  
新建efi挂载点文件夹  
``` bash
mkdir -p /mnt/boot/efi
```
然后挂载
### 安装基本系统
``` 
pacstrap /mnt linux-zen linux-firmware linux-zen-headers base base-devel neovim base-completion networkmanager dhcpcd
```
### 写进分区表
``` 
genfstab -U /mnt >> /mnt/etc/fstab
```
### 进系统&安装引导
用arch-chroot进系统然后安装grub引导  
``` bash
arch-chroot /mnt
pacman -Sy
pacman -S grub efibootmgr efivar intel-ucode os-prober ntfs-3g
```
到`/etc/default/grub`取消注释os-prober的一行（一般在最后一行）
``` bash
grub-install /dev/……
grub-mkconfig -o /boot/grub/grub.cfg
passwd root
systemctl enable NetworkManager
exit
reboot
```
### 进入系统
用`nmtui`联网  
`nvim /etc/hostname`写下arch  
在`nvim /etc/hosts`写下  
```
127.0.0.1	localhost
::1		localhost
127.0.1.1	arch.localdomain	arch
```
设置时间  
```
timedatectl set-timezone Asia/Shanghai && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && hwclock --systohc
timedatectl set-ntp true
```
在`/etc/skel/.bashrc写下
```bash
EDITOR='nvim'
```
然后`cp -a /etc/skel/. ~`
重启
### 添加用户
``` bash
useradd --create-home storm
passwd storm
usermod -aG adm,wheel,storage storm
```
`visudo`
删除%wheel ALL=(ALL:ALL) ALL前面的#  
然后重启
### 本地化配置
```
nvim /etc/locale.gen
```
编辑/etc/locale.gen文件,删除en_US.UTF-8 UTF-8和zh_CN.UTF-8 UTF-8前面的#  
`locale-gen`  
`nvim /etc/locale.conf`  
写下LANG="en_US.UTF-8"  
重启
### 安装plasma
安装核显驱动 
``` 
pacman -S mesa xf86-video-intel vulkan-intel
```
安装plasma
```
pacman -S plasma plasma-meta konsole dolphin kate ark gwenview vlc firefox
firefox-i18n-zh-cn packagekit-qt5
systemctl enable sddm
```
重启后就可以了

---
[返回到上一页](https://storm-1614.github.io/blog-linux/)  
[返回到主页](https://storm-1614.github.io/)
