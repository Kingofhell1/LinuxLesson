1. Доработайте приложенный скрипт из 4-го урока так, чтобы он выводил только чётные значения переменной $num. 
```
#!/bin/bash
num=0
while [ $num -lt 10 ]
do

        num=$(expr $num + 1)
        del=$(($num % 2))
        if [ $del -eq 0 ]
        then
                echo $num $(fortune)
        else
                continue
        fi  
done
```
___
2. Как сделать так, чтобы команда fortune | cowsay -f tux выполнялась автоматически каждый раз, когда вы запускаете консоль? Для подсказки можно обратиться к уроку, в котором мы познакомились с командой alias. Для сдачи подготовьте скриншот с изменениями, которые вы сделали, и результат работы.
``` 
#!/bin/bash
while true
do
echo "Who do you want advice from?"
cat << options
bunny
tux
daemon
kitty
vader-koala
print "quit" to exit
options

        echo
        read -p "MaKe your choice: " option
        if [ $option == "quit" ]
        then
                break
        fi
        echo
        fortune | cowsay -f $option
done
```

3. В четвёртом уроке мы написали скрипт, который выводит псевдографическую картинку с фразой. Сделайте так, чтобы этот скрипт завершался, если пользователь вводит quit.

```
#!/bin/bash
num=0
while [ $num -lt 7 ]
do
mkdir /tmp/HomeWork-$(date "+%Y%m%d %H%M")
num=$(expr $num + 1)
sleep 420
done
```
4. Напишите скрипт, который после запуска должен начать создавать папки в директории /tmp, имена которых должны формироваться по шаблону: directory-YYYYMMDD_HHMM. Папки должны создаваться раз в семь минут, скрипт должен закончиться после того, как создаст минимум семь папок.
