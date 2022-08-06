# VIM в терминале

# vim based terminal
set -o vi
source ~/.bashrc

##### Настройка VIM в терминале как основного редактора
'add the following to your .bashrc :'        
export VISUAL=nvim;
export EDITOR=nvim;

##### Главное управление
`:q!` -  выйти без сохранения      
`:wq`или `ZZ` - записать файл и выйти       
`w`   - записать     
`u`   - отмена последекго действия   
`:r имя` - добавить файл в текущий     
`:r! команда консоли` - выполнить команду и добавить вывод сюда    
`u`  - откат изменений     
`U`  - откат всех изменений  в строке      
`CTRL+R` - отмена отката     

##### Окна 
`Cntrl+W, S` - создать окно
`Cntrl+W, <- ->` -  Перемещение по окнам
`:vsp` - vertical split
`:hsp` - horisontal split

##### Дирректории
`:e .` - current dirrectory
`:e ~/home` - home

##### Управление курсором
`hjkl` -перемещения        
`w,b,4w,4b` - следующее/предыдущее слово / несколько слов     `0/$` - начало/конец строки     
`qq/G` - начало/конец файла    
`"``"`- предыдущее место курсора        
`e`   - курсор в конце слова
`(/)` - перемещение по предложениям
`{/}` - перемещение по обзацам

##### Ввод
`i` - ввод по курсору    
`I` - ввод с начала строки 
`a` - ввод после курсора    
`A` - ввод с конца строки 
`A` - ввод в конец строки     
`o` - ввод со строки под курсором     
`O` - ввод со строки над курсором    
`R` - режим замены
`r` - заменить один символ

##### Копирование
`gg+VG`- веделение всего контента
`v`   - режим выделения текста     
`y`   - скопировать символы    
`yy`  - скопировать строку целиком     
`p`   - вставить символы скопированные или только что удаленные   
`v`   - выделение текста стрелками
`Shift+v`  - строка целиком
`Ctrl+v`   - прямоугольник целиком 


##### Удаление 
`D`  - удалить от курсора до конца строки    
`dd` - удалить всю строку     
`x`  - удалить символ под курсором      

##### Поиск
`/`  - поиск от курсора до конца документа
`?` - поиск от курсора до начала документа
`CTRL+R` - поиск в противоположном направлении
`n`  - перейти к следующему вхождению
`N`  - к предыдущему вхождению
`%`  - парная строка
`:noh`- отмена поиска

##### Замена 
`:[range]s/{pattern}/{string}/[flags] [count]`
```shell
"%" - символ всех строк
"s" - строка
"g" - все вхождения
"gi" - игнорировать регистр
```
  `:%s/было/стало/` - в первом вхождении     
  `:%s/было/стало/g` - во всем файле     
  `:s/foo//g` - если / опущена, то вхождение удаляется
 Подсветка всех изменений при поиске - `:set hls` - отключение - `:set nohls`   
 Игнорирование регистра при поиске - `:set ic` - отключение - `:set noic`   
 Отображение частичных совпажений при поиске - `:set is` - отключение - `:set nois`   

##### Межфайловое взаимодействие
`:e /path/to/other/file` - открыть в том же окне VIM
`vi -o /path/to/file1 /path/to/file2` - открыть в сплит-окне 
 Ctrl + w, Up/Down  - переходы
 Ctrl + w, S  - открыть сплит-окно в текущем файле

# VIMium into browser

##### Navigating history
```shell
H	:	Go back in history
L	:	Go forward in history
Manipulating tabs
K, gt	:	Go one tab right
J, gT	:	Go one tab left
t	:	Create new tab
x	:	Close current tab
X	:	Restore closed tab
```

##### Navigating the page
```shell
?	:	Show the help dialog
j	:	Scroll down
k	:	Scroll up
h	:	Scroll left
l	:	Scroll right
gg	:	Scroll to the top of the page
G	:	Scroll to the bottom of the page
u, <c-u>	:	Scroll a half page up
d, <c-d>	:	Scroll a half page down
<c-f>	:	Scroll a full page down
<c-b>	:	Scroll a full page up
f	:	Open a link in the current tab
F	:	Open a link in a new tab
o	:	Open URL, bookmark, or history entry
O	:	Open URL, bookmark, or history entry in a new tab
r	:	Reload the page
gs	:	View page source
/	:	Enter find mode
n	:	Cycle forward to the next find match
N	:	Cycle backward to the previous find match
yy	:	Copy the current URL to the clipboard
gf	:	Cycle focus to the next frame
i	:	Enter insert mode
```
