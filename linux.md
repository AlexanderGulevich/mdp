## Эмулятор терминала 
```shell


```

```bash
По сути, tilix, является программой (эмолятором терминала), которая взаимодействует с командной оболочкой. Командная оболочка - это по, которое позволяет принимать команды и передавать операционной системе. Сейчас везде bash такая оболочка. Она является улучшенной заменой sh (shell).
```

## Bash
```bash
sudo su  #стать суперпользователемЖ
sudo -s  #запустить shell от админа

-$  - приглашение к вводу
-# - ввод от суперпользователя 

CNTRL+A / E # начало и конец строки
ALT+.   # использование аргумента предыдущей команды
CNTRL+C # прерывание команды
CNTRL+D # покинуть терминал
yes | comand  # ввод ДА заранее

# запуск нескольких команд за раз
command_1; command_2; command_3
# запуск нескольких команд за раз ПАРАЛЕЛЬНО
(command_1 &); (command_2 &)
# запуск нескольких команд за раз, при условии ПРЕДЫДУЩАЯ БЕЗ ОШИБКИ
command_1 && command_2
# загрузка множества пакетов по порядку
sudo apt-get install package-x package-y

cd ~ #home
cd   #home
cd - # предыдущ  рабоч каталог 
cd / # корневой

file <file> #type of file

ls #list of files
ls -l #long type of info 
ls -a #all files and catalogs
ls -S #sort by size 
ls -r #reverse 
ls -t #by time


пробел перед командой и она не сохранится в истории 

cal 2021 #календарь

curl wttr.in/<нужный город> # weather

watch <команда> #  Многократный запуск команды
time <команда> # Узнать время на запуск команды
strace <команда>.#  Системные вызовы команды
wget --random-wait -r -p -e robots=off -U mozilla <адрес сайта>.#  Выкачиваем сайты



```


## Полезные мелочи
```bash
reboot   #перезагрузка
poweroff #выключить комп
killall chrome # убить процесс и все связанные с ним

# создать туннель от 80 порта на удалённой машине до 2001 на локальной.
ssh -N -L 2001:localhost:80 somemachine

xdg-open XXX      #Открыть файл приложением по умолчанию

apropos  command  #find smthg
whatis ls         #short info about programs
whereis gcc       #более полная инф о расположении ПО
locate vim        #еще более
which node        #Получить путь расположения ИСПОЛНЯЕМОЙ программы, не встроенной в оболочку
type ls           #тип комманды 
help cd           #inf about bash commands
mkdir --help      #info about programm
man mkdir         #info
file              #info about file 
history
info ls

# распаковать архив
tar zxvf jre-8u73-linux-x64.tar.gz



```

## Права
`r` - читать `w` - запись `x` - выполнение `s` - выполнение от суперпользоавтеля

`u` владелец группы `g` - группа файла `o` -все остальные пользователи

`0`никаких прав `1`только выполнение `2`только запись `3`выполнение и запись`4`только чтение `5` чтение и выполнение`6`чтение и запись `7`чтение, запись и выполнение

`chmod u+x file`
`chmod 766 file`
`chmod ugo-rwx file`
`chmod -R ug+rw dir`
`chmod -Rv ug+rw dir`

_Во время установки прав сначала укажите цифру прав для владельца, затем для группы, а потом для остальных_

-c - выводить информацию обо всех изменениях;
-f - не выводить сообщения об ошибках;
-v - выводить максимум информации;
--preserve-root - не выполнять рекурсивные операции для корня "/";
--reference - взять маску прав из указанного файла;
-R - включить поддержку рекурсии;
--version - вывести версию утилиты;



## Работа с alias	
```java
vim ~/.bashrc 
alias msrv='cd ~/yandex/msrv'
alias msrvi='cd ~/yandex/msrv; markserv'
или
alias msrvi='cd ~/yandex/msrv; markserv --livereloadport 35728'

alias me='cd ~/me'

```


## SWAP
```bash
# to see
free -h
swapon -show

#on/off
sudo swapoff -a && swapon -a

#delete
sudo swapoff /swapfile
sudo rm /swapfile

#create
sudo fallocate -l 8G /swapfile
#rights
sudo chmod 600 /swapfile
#file system
sudo mkswap /swapfile
#activate
sudo swapon /swapfile
#write into etc/fstab for reboot not deniying swap
/swapfile none swap sw 0 0


```

## Поиск
```bash
find which locate grep sed

```

## Освободить порт 
```bash
lsof -i:4200

kill -9 PID
```

## Информация о системе
```java
// сенсоры температуры
sudo apt install lm-sensors hddtemp
sudo sensors-detect
sensors

uname -a
sudo lshw     // аппаратное обеспечение 
lscpu         //информация об процессоре
lsblk -p      // список дисков и их разделов
lspci	      //инф о всех шинах PCI а также о всех устройствах, присоединенных к этим шинам, видеокартам, сетевым адаптерам)
lspci -t      //инф в виде дерева
lspci -v      //инф о каждом подключкнном устройстве
lsscsi	      // Вывести список устройств scsi/sata
sudo fdisk -l // о списке имеющихся разделов
sudo dmidecode -t memory // об оперативной памяти
sudo dmidecode -t bios // о биос
sudo dmidecode -t processor // о процессоре
lsusb          // о каждом подключенном устройстве
free -m        // свободная оперативка в системе
lscpu          // инфо о процессоре
neofetch       // базовая информация о дистрибутиве
lshw  || hwinfo || lspci  || inxi		// info about hardware

pydf || df                // доступное дисковое пространство
du -sh   ./nameOffolder   // размер папки
du -sh ./Загрузки/*       // размер всех подпапок

```
## Файлы и каталоги

```java
touch filename.ext //Создание файла
cat > filename.ext // для выхода из режима записи CNTRL+d
echo > filename.ext
vim filename.ext

tar -xvf archive.tar // unpack archive


mkdir // create folder 

cp element folder # copy 
// cp -i /etc/password .
cp -a // with all attributes
cp -r //recursive
cp -v // with logs
cp -u // only not existed in destination folder cp -i // requre apply to records matched files

mv #move
// mv -i /etc/password .
mv -v // with logs
mv -u // only not existed in destination folder
mv -i // requre apply to records matched files

mv old.ext new.ext //Переименование файла

rm #delete
rm -r //recursive
rm -v // with logs
rm -f // ignore all and delete 
rm -i // requre appliying 

// Символическая ссылка 
//можно ссылаться на каталоги 
//при удалениии всех ссылок файл не удаляется
ln -s /home/me/one.txt dir/one-sym.txt

//Жесткая ссылка 
//При удалении всех ссылок файл тоже удалится
ln  /home/me/one.txt dir/one-sym.txt

```

## Групповые символы

```java
b*.txt  // 
[abc] // все с abc
data??? // data + 3 любых символа
backup.[0-9] [0-9] [0-9] // после точки три цифры
[![:digit:]]* // все имена, не начинающиеся с цифры
*[[:lower]123] // все имена, что заканчиваются буквой в нижнем регистре и цифрами 123
[:alnum] // алфавитно цифровой символ
[:alpha] // алфавитный символ
[:upper] // верхнего регистра 


```
    
## Окружение 
```java
//Добавление переменной окружения
cd $HOME
vim .bashrc 
export PATH=/usr/java/<JDK Directory>/bin:$PATH
выйти и	сохранить
source .bashrc              
```
*Note that if you wish to set the PATH for all users, you need to log in as root in the bash shell and perform the above steps on the .profile file in the etc directory and not the __.bashrc__ file in the home directory.*

```java
//Добавление переменной только на время сессии терминала        
export PATH=$PATH:/path/to/dir
```
```java
//FILES

// /etc/environment       
Perfect for adding system-wide directories like
/usr/local/something/bin to PATH variable 
or defining JAVA_HOME. Used by PAM and SystemD.         

// /etc/environment.d/*.conf           
List of unique assignments Perfect for adding system-wide directories
like /usr/local/something/bin to PATH variable or defining JAVA_HOME.
The configuration can be split into multiple files,
usually one per each tool (Java, Go, NodeJS).
Used by SystemD that by design do not pass those values to user login shells.       

// /etc/xprofile        
Shell script executed while starting X Window System session.
This is run for every user that logs into X Window System.
It is a good choice for PATH entries that are valid for every user
like /usr/local/something/bin. The file is included by other script
so use POSIX shell syntax not the syntax of your user shell.

// /etc/profile and /etc/profile.d/*            
Shell script. This is a good choice for shell-only systems.
Those files are read only by shells in login mode.

// /etc/<shell>.<shell>rc.         
Shell script. This is a poor choice because
it is single shell specific. Used in non-login mode.
```
## USB

```java
// Форматировать флешку:     
df  //  вывод дисков  
sudo umount /dev/XXX   //  отмонтировать         	  
sudo mkfs.vfat -n 'Name' -I /dev/XXX           	
//другие файловые системы -  mkfs.ext4, mkfs.msdos, mkfs.vfat         	   
```

```java
// Восстановление флешки после ISO образа:   
sudo parted -l       // показать разделы 
fdisk -l             // найти имя монтирования (sdb например)
fdisk /dev/sd(x)     // 
d		     // to proceed to delete a partition
1		     // to select the 1st partition
d		     // to proceed to delete another partition
n		     // to make a new partition
p		     // to make this partition primary 
1		     // to make this the first partition
w		     // to write the new partition info to the USB 
umount /dev/sd(x)1
sudo mkfs.vfat -F 32 /dev/sd(x)1
```

## Mounting
```java
mount // список монтированных устройств
sudo mount /dev/sdb6 /mnt/   // монтировать 
sudo mount -v /dev/sdb6 /mnt/     // монтировать с комментами о процессе
sudo mount -v -t ext4 /dev/sdb6 /mnt   // монтирвать в опрелеленную файловую систему
sudo mount --label="home" /mnt/    // 

sudo umount /mnt   // размонтировать
lsof -w /mnt  //показыть чем занято устройство 
sudo umount -l /mnt   // отмонтировать даже если занято

// разрешить читать и записывать 
sudo chown $USER: /home/usb 

```



## Пакетные менеджеры
```java

// PACMAN

pacman -S XXX    // установка     
pacman -Syu      // полное обновление системы    
pacman -Ss XXX  // 	поиск
pacman -U /путь/к/пакету/имя_пакета-версия.pkg.tar.xz    //Установить локальный пакет     

pacman -Rs //удаления локального пакета, если он не используется другими пакетами
pacman -Qs eclipse //поиск установленных пакетов eclipse



```

```java
// YAY
yay -S   XXX   // установить пакет
yay -Ss  XXX   // поиск пакета в официальных репозиториях
yay -Si  XXX   // поиск в aur  и официальных репозиториях
yay -Syu       // обновить все пакеты из aur
yay mplayer    // выберется меню выбора пакета при установке
yay -Ps	       // печатать статистику
```

## Сеть
```java
sudo lsof -i :80 // показать, чем занят порт
```

# Java
```bash
java --version

which java

# работа с окружением java в arch 
archlinux-java

java -XshowSettings:properties -version 2>&1 > /dev/null | grep 'java.home'
```

## РАЗНЫЕ ПРОГРАММЫ

### audio/video 
```bash
# youtube-dl
youtube-dl -x --audio-format mp3  
youtube-dl -x --audio-format mp3 --playlist-start 1 --playlist-end 5
youtube-dl -x --audio-format mp3 --audio-quality 0
youtube-dl -x --audio-format mp3 --audio-quality 0 --playlist-start  --playlist-end  


# Вырезать аудил из видео и конвертировать
ffmpeg -i input.mp4  -c:a copy aac.aac ; ffmpeg -i aac.aac output.mp3


pdfunite file1.pdf file2.pdf mergedfile.pdf
```
### tomb



### Clone hard drive
```shell


```

```shell


```


```shell


```



```shell


```


