
# ARCH LINUX

## Check Internet
 `ping -c 3 google.com` 
 `wifi-menu`

## Update systemclock
 `timedatectl set-ntp true`
 `timedatectl status`

## Media drives
 `lsblk` - list of disks
 `fdisk -l` - second type of list

 `cfdisk /dev/sda` - partition
1. SWAP - 8G - sda1: new -> primary
2. BootPartition - 512M - sda2: new -> primary-> bootable
3. RootPartition -  - sda3: new -> primary

 `mkswap /dev/sda1`	
 `swapon /dev/sda1`

 `mkfs.vfat /dev/sda2`
 `mkfs.ext4 /dev/sda3`
 
 `mount /dev/sda3 /mnt`
 `mkdir /mnt/home`
 `mkdir /mnt/boot`
 `mount /dev/sda2 /mnt/boot`

## Mirrors
 `pacman -Syy`
 `nvim /etc/pacman.conf`
 `pacman -S reflector`
 `cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.bak`
 `reflector -c "XX" -f 12 -l 10 -n 12 --save /etc/pacman.d/mirrorlist`

## Install the main packgages
 `pacstrap -i /mnt base base-devel linux linux-firmware sudo neovim`
 `genfstab -U -p /mnt >> /mnt/etc/fstab`   - create fstab file with media boot targets 
 `arch-chroot /mnt`  - log in system

## Locale
 `sudo nvim /etc/locale.gen` - uncomment LANG=en_US.UTF-8  and LANG=ru_RU.UTF-8
 `locale-gen
 `locale -a`  - view all locales
 `echo [LANG=en_US.UTF-8] > /etc/locale.conf
 `export LANG=en_US.UTF-8` 
 `echo "KEEYMAP=us" >> /etc/vconsole.conf`

## Sync time
 `timedatectl list-timezones`
 `timedatectl set-timezone Europe/Minsk`
 `hwclock --systohc --utc`
 `date`

## Host 
 `echo [comp_name] > /etc/hostname`
 `vim /etc/hosts`
 `  127.0.0.1	localhost`
 `  ::1		localhost`
 `  127.0.1.1 localhost.localdomain NameOfComp`

## Network
 `pacman -S networkmanager dhcpcd`
 `systemctl enable NetworkManager` 
 `systemctl enable dhcpcd`
 
## set root password
 `passwd`
 
## inst sudo and bash-complection
 `pacman -S sudo bash-comletion`

## Add users
`useradd -m -g users -G wheel, storage, power, log -s /bin/bash USERNAME`
`passwd USERNAME`
__/etc/sudoers__
_Uncomment to allow members of group wheel to execute any command_
`%wheel ALL=(ALL:ALL) ALL`
_Uncomment to allow members of group sudo to execute any command_
`%sudo  ALL=(ALL:ALL) ALL`

## Instull grub
 `mkinitcpo -p linux`
 `pacman -S grub os-prober`
 `grub-install /dev/sda`
 `grub-mkconfig -o /boot/grub/grub.cfg
 `exit
 `unmount /mnt`
 `sudo reboot


# POST-INSTALLING

### i3wm
sudo pacman -S xorg-server xorg-xinit i4-gaps i3status rofi
echo 'exec i3' >> ~/.xinitrc
startx

bindsym $mod+d exec --no-startup-id rofi -show run
rofi-theme-selector


`sudo pacman -S nitrogen`
__/home/alex/.config/i3/config__
`exec --no-startup-id nitrogen`


sudo pacman -S picom   - странная фича, зависает арч

## Monitors
`sudo pacman -S xorg-xrandr`

__/home/alex/.config/i3/config__
`exec xrandr --output eDP-1 --mode 1920x1200 --pos 0x0`
`exec xrandr --output HDMI-2 --mode 1920x1080 --pos 1920x0`

__OFF__
`xrandr --output HDMI-2 --off`
__ON__
`xrandr --output HDMI-2 --mode 1920x1080 --pos 1920x0`

### Fonts
sudo pacman -S ttf-hack ttf-ubuntu-font-family  ttf-liberation ttf-dejavu opendesktop-fonts ttf-bitstream-vera ttf-arphic-ukai ttf-arphic-uming ttf-hanazono noto-fonts ttf-font-awesome 

### Coloraised pacman
sudo vim /etc/pacman.conf

### For NTFS mounting
sudo pacman -S ntfs-3g

### Keymap 
`sudo pacman -S setxkbmap`
`vim ~/.config/i3/config`
`exec --no-startup-id setxkbmap us,ru -option 'grp:alt_shift_toggle'`

__~/.xprofile__
`setxkbmap -option grp:alt_shift_toggle -layout us,ru &`

__~/.xnitrc__
`[ -f ~/.xprofile ] && . ~/.xprofile`
`sudo pacman -S xorg-setxkbmap`
`source .xprofile`

### Display manager -- CDM --


### SOUND
`pacman -S pipewire pipewire-pulse pipewire-alsa  pipewire-jack pavucontrol`
`yay jamesdsp`

`pactl info` - проверка

systemctl --user enable pipewire.service
systemctl --user start pipewire.service

systemctl --user enable pipwire-pulse.service
systemctl --user start pipwire-pulse.service

### BlueTooth
`sudo pacman -S bluez bluez-utils blueman blueberry`
__проверка__
`sudo systemctl status bluetooth.service`
__старт для этой сессии__
sudo systemctl start bluetooth
__запуск__
sudo systemctl enable bluetooth
`sudo systemctl start bluetooth.service`
__включение службы для автозапуска__
`sudo systemctl enable bluetooth.service`

### Great APP
sudo pacman -S git firefox google-chrome-stable tilix glow cmus moc ranger htop gtop ypoutube-dl gnome-chess gnuchess neovim nomacs translate-shell xfce4-screenshooter

### Screenshots
yay maim xclip 

```bash

## Screenshots
__/.i3/config__

bindsym Print exec --no-startup-id maim "/home/$USER/Pictures/$(date)"
bindsym $mod+Print exec --no-startup-id maim --window $(xdotool getactivewindow) "/home/$USER/Pictures/$(date)"
bindsym Shift+Print exec --no-startup-id maim --select "/home/$USER/Pictures/$(date)"

## Clipboard Screenshots
bindsym Ctrl+Print exec --no-startup-id maim | xclip -selection clipboard -t image/png
bindsym Ctrl+$mod+Print exec --no-startup-id maim --window $(xdotool getactivewindow) | xclip -selection clipboard -t image/png
bindsym Ctrl+Shift+Print exec --no-startup-id maim --select | xclip -selection clipboard -t image/png

```

### YAY
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si

# Настройка VIM в терминале как основного редактора
'add the following to your .bashrc :'        
export VISUAL=nvim;
export EDITOR=nvim;

### Личный список хороших программ

Намименование  | Описание                                                | Установка        | Запуск
---|---|---|---
Glow           | программа для отображения в темминале markdown разметки | yay -S glow      |
Moc            | music player                                            | pacman -S moc    | mocp
ranger         | терминальный файловый менеджер                          |                  | 
htop           | мониторинг системы                                      |                  |
gtop           | мониторинг системы                                      |                  |
youtube-dl     | download                                                |                      |
 

### Набор установки для обычного джентельмена

okular
fontforge
pamac
thunar

xev    -- название клавишь

//яркость экрана 
xorg-xbacklight    

typora
gnome-chess
viber
telegram

sdkman --- from site

//темы
lxappearance

gvfs
udiskie

