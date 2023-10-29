## LinuxLesson5

####  1 Настроить статическую конфигурацию (без DHCP) в Ubuntu через ip и netplan.
#### 2 Настроить IP, маршрут по умолчанию и DNS-сервера (1.1.1.1 и 8.8.8.8).
#### 3 Проверить работоспособность сети.
 * touch 03-static-networkd.yaml - создаем файл с расширением yaml
 * sudo nano 03-static-networkd.yaml - открываем редактор для изменения конфигурации сети 
   * network:
     - version: 2 
     - renderer: networkd
     - ethernets:
       - enp0s3:
       - dhcp4: no
       - addresses: [192.168.0.8/24]
       - routes: 
           - to: default
           - via: 192.168.0.254
       - nameservers:
         - addresses:
             - 8.8.8.8
             - 1.1.1.1
 * sudo ip addr add 192.168.0.9/255.255.255.0 broadcast 192.168.0.255
 * dev enp0s3
 * ping ya.ru

#### Настроить правила iptables для доступности сервисов на TCP-портах 22, 80 и 443.
 * iptables -A INPUT -i lo -j ACCEPT - установка обратной связи
 * iptables -A INPUT -p tcp --dport=22 -j ACCEPT - установка порта 
 * iptables -A INPUT -p tcp --dport=80 -j ACCEPT - установка порта
 * iptables -A INPUT -p tcp --dport=443 -j ACCEPT - установка порта
#### Также сервер должен иметь возможность устанавливать подключения к серверу обновлений.
 * iptables -I INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT 
#### Остальные подключения запретить.
 * iptables -P INPUT DROP
#### Запретить любой входящий трафик с IP 3.4.5.6.
 * iptables -I INPUT -s 3.4.5.6 -j DROP -запрет с ip
#### Запросы на порт 8090 перенаправлять на порт 80 (на этом же сервере).
 * iptables -t nat -I PREROUTING -p tcp --dport 8090 -j REDIRECT
#### Разрешить подключение по SSH только из сети 192.168.0.0/24.
 * iptables -I INPUT -p TCP --dport 22 -j DROP
 * iptables -I INPUT -p TCP --dport 22 -s 192.168.0.0/24 -j ACCEPT