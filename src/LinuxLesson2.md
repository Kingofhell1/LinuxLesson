## LinuxLesson1
#### Используя команду cat, создать два файла с данными, а затем объединить их.
   * cat > file.txt - создаю файл с записью в него 
   * cat > file2.txt -  создаю файл с записью в него 
   * cat file.txt file2.txt > file3.txt - объкдинение файлов 
#### Просмотреть содержимое созданного файла.
   * cat file3.txt - просмотр файла, либо cat -n file3.txt - просмотр файла с нумирацией строк 
#### Переименовать файл, дав ему новое имя. 
   * mv file3.txt NewFile - переименовать файл
#### Создать несколько файлов.
   * touch file5.txt file6.txt - создание несколько пустых файлов
#### Создать директорию, переместить файл туда.
   * mkdir file_lnk - создание нового директория
   * mv file5.txt /home/dmitriy/file_lnk - перемещение файла в новую дирикторию
   * mv file6.txt /home/dmitriy/file_lnk - перемещение файла в новую дирикторию
#### Удалить все созданные в этом и предыдущем задании директории и файлы.
   * rm -rf file_lnk - удалит директорий и сами файлы хронящиеся в данном директории
#### Создать файл file1 и наполнить его произвольным содержимым.
   * cat > file1.txt - создания файла с записью в него 
#### Скопировать его в file2.
   * cp file1.txt temdir/file2.txt - копирую файл в другую директорию  в новый файл
#### Создать символическую ссылку file3 на file1.
   * ln -s file1.txt file3.txt - создание ссылки на другой файл
#### Создать жёсткую ссылку file4 на file1.
   * ln file1.txt file4.txt - создание ссылки на другой файл
#### Посмотреть, какие айноды у файлов.
   * ls - ali -посмотреть inode одинаковые или нет.
#### Удалить file1.
   * rm /home/dmitriy/file1.txt
#### Что стало с остальными созданными файлами?
   * cat: file3.txt: Нет такого файла или каталога
   * Жесткие ссылки остались неизменны, файл file4 cохранит информацию от file1, но потеряет ссылку, а ссылочные ссылки стали красными, file3 перестал ссылаться на file1 и получать данные от туда поэтому ссылка (он ссылается в никуда)
#### Попробовать вывести их на экран.
   * При выведении file3 выводит ошибку, так как симмвольная ссылка ссылается на пустоту. Файлы привязанные жесткой ссылкой работают и можно вносить изменения.
#### Дать созданным файлам другие, произвольные имена.
   * mv file4.txt fileFile.txt
   * mv file2.txt file_ln.txt
#### Создать новую символическую ссылку.
   * ln -s /home/dmitriy/file1_1.txt file6.txt
#### Переместить ссылки в другую директорию.
   *  ln -s file6.txt /home/dmitriy/temdir/file1.txt