## LinuxLesson2
#### Создать два произвольных файла.
* touch file1.txt - создание произвольного файла
* touch file2.txt - создание произвольного файла
#### Первому присвоить права на чтение и запись для владельца и группы, только на чтение — для всех.
* chmod u=rw,g=rw,o=r file1.txt - сиимвольный
* chmod 664 file1.txt - числовой
#### Второму присвоить права на чтение и запись только для владельца. Сделать это в численном и символьном виде.
* chmod u=rw,g=,o= file2.txt - символьный
* chmod 600 file.txt - числовой
#### Назначить новых владельца и группу для директории целиком.
*  sudo chown -R testuser:www-data /home/dmitriy/temdir - назначение в дирикторию новго польззователя и группы
### Управление пользователями:
#### создать пользователя, используя утилиту useradd и adduser;
*  sudo useradd -s /bin/bash -m -d /home/testuser testuser - создание новго пользователя
*  sudo adduser testuser2 - добавление нового пользователе
#### удалить пользователя, используя утилиту userdel.
* sudo userdel -r testuser2 - удаление пользователя со всеми файлами
### Управление группами:

#### создать группу с использованием утилит groupadd и addgroup;
* sudo groupadd testgroup - создание группы
#### попрактиковаться в смене групп у пользователей;
* sudo adduser testuser2 - создаем пользователя
*  sudo groupadd testgroup - создание группы
*  sudo usermod -g testgroup testuser2 - присвоение группы к пользователю
#### добавить пользователя в группу, не меняя основной;
* sudo usermod -G testgroup1 testuser2
* groups testuser2
#### Создать пользователя с правами суперпользователя. Сделать так, чтобы sudo не требовал пароль для выполнения команд.
* sudo vision - заходим в редактор, но нужно быть осторожным, можно лишиться правами sudo
* %sudo ALL=(ALL:ALL) NOPASSWD:ALL - делаем доступ без пароля
  Дополнительные (необязательные) задания

• Используя дополнительные материалы, выдать одному из созданных пользователей право на выполнение ряда команд, требующих прав суперпользователя (команды выбираем на своё усмотрение).

#### Создать группу developer и нескольких пользователей, входящих в неё.
* sudo groupadd developer
* sudo useradd -m user1 -G developer
* sudo useradd -m user2 -G developer
* sudo useradd -m user3 -G developer
#### Создать директорию для совместной работы.
* sudo mkdir /shared
* sudo chown root:developer /shared
* sudo chmod 770 /shared
#### Сделать так, чтобы созданные одними пользователями файлы могли изменять другие пользователи этой группы.
* sudo chmod +t /shared
#### Создать в директории для совместной работы поддиректорию для обмена файлами, но чтобы удалять файлы могли только их создатели.
* sudo mkdir /shared/filess
* sudo chown root:developer /shared/files
* sudo chmod 770 /shared/files
* sudo chmod +t /shared/files
  • Создать директорию, в которой есть несколько файлов.
  Сделать так, чтобы открыть файлы можно было, только зная имя файла, а через ls список файлов посмотреть было нельзя.