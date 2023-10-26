## LinuxLesson4

Все пишу без sudo, так как зашел через пользователя root (sudo su)
#### Подключить дополнительный репозиторий на выбор: Docker, Nginx, Oracle MySQL. Установить любой пакет из этого репозитория.
  * apt search nginx - ищем пакеты, которые нужны для установки либо выводим список apt list nginx - ищем конкретные файлы
  * apt install nginx - установка репозитория, но потребуется подтвердить нужно ли устанавливать, чтобы это предотварить используем apt install -y nginx
#### Установка Докера
  *  sudo apt install curl 
  * sudo install -m 0755 -d /etc/apt/keyrings
  *  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
  *  echo \
     "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
     "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
     sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  * sudo apt update
  *  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-com
     pose-plugin
  * sudo docker run hello-world
  * Unable to find image 'hello-world:latest' locally
    latest: Pulling from library/hello-world
    719385e32844: Pull complete
    Digest: sha256:88ec0acaa3ec199d3b7eaf73588f4518c25f9d34f58ce9a0df68429c5af48e8d
    Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
1. The Docker client contacted the Docker daemon.
2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
   (amd64)
3. The Docker daemon created a new container from that image which runs the
   executable that produces the output you are currently reading.
4. The Docker daemon streamed that output to the Docker client, which sent it
   to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
$ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
https://hub.docker.com/

For more examples and ideas, visit:
https://docs.docker.com/get-started/
* systemctl status docker
*  docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2023-10-26 22:43:58 MSK; 3min 18s ago
   TriggeredBy: ● docker.socket
   Docs: https://docs.docker.com
   Main PID: 19770 (dockerd)
   Tasks: 11
   Memory: 32.1M
   CPU: 7.526s
   CGroup: /system.slice/docker.service
   └─19770 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock

#### Установить и удалить deb-пакет с помощью dpkg.
  *  wget https://download.virtualbox.org/virtualbox/7.0.12/virtualbox-7.0_7.0.12-159484~Ubuntu~jammy_amd64.deb  - скачиваем файл
  *  dpkg -i virtualbox-7.0_7.0.12-159484~Ubuntu~jammy_amd64.deb - установка пакетов из загрузки.
  *  apt -f install - устанавливаем виртуалбокс.
  *  dpkg -r virtualbox-7.0 - удалене пакета
  *  apt autoremove - удаление оставшихся файлов
#### Установить и удалить snap-пакет.
  *   snap install htop - установка диспетчера задачь 
  *   snap remove htop - удаление диспетчера задачь
#### Добавить задачу для выполнения каждые 3 минуты (создание директории, запись в файл).
  * crontab -e - отркываем редактор планирования записываем туда 3 * * * * mkdir /tmp/test && date > /tmp/test/date.txt
  * crontab -r -i - для удаление планирования
#### Подключить PPA-репозиторий на выбор. Установить из него пакет. Удалить PPA из системы.
  * add-apt-repository ppa:ondrej/php - добавления репозитория php.
  * apt install php8.1 - устанавливаем пакет php
  * apt update - обновления файловой системы
  * apt remove php8.1 - удаление пакетов.
#### Создать задачу резервного копирования (tar) домашнего каталога пользователя. Реализовать с использованием пользовательских crontab-файлов.